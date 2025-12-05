---
{"dg-publish":true,"permalink":"/01-reference/connect-to-android-over-ssh/","title":"Connect to Android using SSH and Termux","tags":["linux","network","ssh"],"created":"2025-12-05T03:27:51.079+01:00"}
---


# Connect to Android using SSH and Termux

This guide explains how to connect to your Android device from a Linux desktop using SSH (Secure Shell), with the help of the Termux app. SSH allows you to securely access your phone's command-line environment remotely from another machine on the same network.

---

## Step 1: Install and Configure SSH in Termux

1. Open the Termux app on your Android phone.
2. Update and upgrade Termux packages:

   ```bash
   pkg update && pkg upgrade
   ```

3. Install the OpenSSH package:

   ```bash
   pkg install openssh
   ```

4. Start the SSH daemon:

   ```bash
   sshd
   ```

   To stop the server later, run:

   ```bash
   pkill sshd
   ```

---

## Step 2: Find Your Android Device's IP Address

1. Make sure your Android phone and Linux desktop are connected to the same Wi-Fi network.
2. In Termux, run:

   ```bash
   ip address
   ```

3. Look for the `inet` address under the `wlan0` interface (typically something like `192.168.x.x` or `10.0.x.x`).

---

## Step 3: Connect to Your Phone from a Linux Desktop

1. On your Linux desktop, open a terminal.
2. Connect to the Android device using:

   ```bash
   ssh -p 8022 username@192.168.x.x
   ```

   Replace `username` with the output of the `whoami` command from Termux (usually `u0_aXXX`) or set a password using:

   ```bash
   passwd
   ```

3. Enter the Termux password when prompted.

---

## Optional: Set Up SSH Key-Based Authentication

To avoid entering your password each time and improve security, set up SSH key-based authentication.

### Generate an SSH Key Pair on Linux

Run the following command on your Linux desktop:

```bash
ssh-keygen -t ed25519
```

Alternatively:

```bash
ssh-keygen -t rsa -b 4096
```

- Accept the default file location.
- Choose whether to set a passphrase.

This creates two files in `~/.ssh/`:
- `id_ed25519` or `id_rsa`: private key
- `id_ed25519.pub` or `id_rsa.pub`: public key

### Copy the Public Key to Your Android Device

Run the following command on your desktop:

```bash
ssh-copy-id -p 8022 username@192.168.x.x
```

If `ssh-copy-id` fails, you can do it manually:

1. On your Linux desktop:

   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```

2. Copy the key to clipboard.
3. Connect to Termux:

   ```bash
   ssh -p 8022 username@192.168.x.x
   ```

4. Inside Termux:

   ```bash
   mkdir -p ~/.ssh
   chmod 700 ~/.ssh
   nano ~/.ssh/authorized_keys
   ```

5. Paste the public key, save and exit.

6. Set permissions:

   ```bash
   chmod 600 ~/.ssh/authorized_keys
   ```

---

## Final Step: Connect Using SSH Key

Use the same SSH command:

```bash
ssh -p 8022 username@192.168.x.x
```

If you set a passphrase, it will be prompted; otherwise, you will be logged in directly.

---

## Summary Table

| Step                      | Command Example                            |
|---------------------------|---------------------------------------------|
| Install OpenSSH           | `pkg install openssh`                       |
| Start SSH server          | `sshd`                                      |
| Get IP address            | `ip address`                                |
| Set password              | `passwd`                                    |
| SSH into device           | `ssh -p 8022 username@192.168.x.x`          |
| Generate SSH keys         | `ssh-keygen -t ed25519`                     |
| Copy SSH key automatically| `ssh-copy-id -p 8022 username@192.168.x.x` |

This setup allows your Android device to function like a lightweight and secure remote-access terminal.
