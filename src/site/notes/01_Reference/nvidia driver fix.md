---
{"dg-publish":true,"permalink":"/01_Reference/nvidia driver fix/","title":"Display issue after Nvidia driver update","tags":["issue","nvidia","ubuntu"],"created":"2025-12-05T03:27:51.077+01:00"}
---


# Display issue after Nvidia driver update

I have repeatedly encountered display resolution issues on my Ubuntu machine, no matter which Ubuntu version i have currently installed, and i had many different versions. There is one thing in common in any of those: **Old version of Nvidia display driver is not removed properly**. Every time i resolve the issue by following both wrong and correct instructions i was very quick to forget both the cause and solution. Now i decided to write it down for my future self as a reference.

> [!warning]+
> _Try not to forget this note exists._

This guide provides step-by-step instructions to completely remove old Nvidia drivers and install the latest recommended version. This process can resolve common issues like incorrect resolution or driver conflicts after an update.

**Important Warning:** This process will temporarily leave you without a graphical user interface (GUI). You must run these commands from a virtual console (TTY), not from a terminal window inside your desktop.

---

### Step 1: Switch to a TTY (Virtual Console)

To safely modify graphics drivers, you need to exit the graphical environment.

1.  Press the key combination `Ctrl+Alt+F3`.
2.  This will switch you to a black screen with a login prompt.
3.  Log in with your username and password. Your desktop session will remain running in the background on another TTY (usually TTY1 or TTY2).

---

### Step 2: Purge All Existing Nvidia Packages

This command will find and completely remove all packages and configuration files related to Nvidia, preventing any conflicts with the new installation.

```bash
sudo apt-get remove --purge '^nvidia-.*' 'libnvidia-.*'
```

After the command finishes, it's a good idea to also run:

```bash
sudo apt autoremove
```

This will remove any leftover dependencies that are no longer needed.

---

### Step 3: Reboot Your System

A reboot is necessary to ensure all old driver modules are unloaded from the kernel.

```bash
sudo reboot
```

After rebooting, your system will likely start with a low-resolution display using the default open-source "Nouveau" driver. This is normal.

---

### Step 4: Install the Recommended Nvidia Driver

Ubuntu has a built-in tool to find and install the best driver for your hardware.

1.  Open a terminal window.
2.  Run the following command to see the list of available drivers and the one recommended for your system:

	```bash
    ubuntu-drivers devices
    ```

3.  To automatically install the recommended driver, run:

	```bash
    # install the recommended driver
    sudo ubuntu-drivers autoinstall
    
    # if recommended driver fails, install specific version
    sudo apt install nvidia-driver-570
    ```

On newer Ubuntu kernels, or after system upgrades, it's possible that the "recommended driver" is not actually compatible, or it needs extra configuration. In those cases try to install the specific version with the above command.

---

### Step 5: Reboot Again

One final reboot is needed to load the newly installed Nvidia driver.

```bash
sudo reboot
```

Your system should now start with the correct resolution and the new Nvidia drivers fully active.

---

### Verification (Optional)

After rebooting and logging in, you can verify that the Nvidia driver is loaded correctly by running this command in a terminal:

```bash
nvidia-smi
```

This command should display a table with information about your Nvidia GPU, the driver version, and any running processes using the GPU. If you see this output, the installation was successful.

---

## Extra steps and suggestions to try

If you suspect the basic instructions aren't enough in your case, consider doing the following **deep clean and reinstall**. It is more aggressive but often effective.

```bash
# 1. Purge NVIDIA drivers
sudo apt-get remove --purge '^nvidia-.*' 'libnvidia-.*'
sudo apt autoremove
sudo apt autoclean

# 2. Remove possible manual-installer leftovers (if you ever used .run installer)
sudo rm -rf /lib/modprobe.d/nvidia-installer-*
sudo rm -rf /etc/modprobe.d/nvidia-installer-*
sudo rm -rf /usr/lib/modprobe.d/nvidia-installer-*
sudo rm -rf /usr/local/cuda*
sudo rm -rf /usr/local/nvidia*
sudo rm -rf /usr/lib/nvidia*
sudo rm -rf /usr/include/nvidia*
sudo rm -rf /etc/systemd/system/nvidia*

# 3. Ensure nouveau (or default open-source driver) can load
sudo rm /etc/modprobe.d/blacklist-nouveau.conf
sudo update-initramfs -u

# 4. Reboot
sudo reboot

# 5. Confirm nouveau is loaded (or at least no nvidia modules are loaded)
lsmod | grep -e nouveau -e nvidia

# 6. Install recommended driver again
sudo apt update
sudo ubuntu-drivers autoinstall
# — or pick a specific driver version:
# sudo apt install nvidia-driver-XXX

# 7. Reboot again
sudo reboot

# 8. Validate
nvidia-smi
lsmod | grep nvidia

```

If after this sequence your system still fails (black screen, low resolution, `nvidia-smi` reports “no devices”, or modules not loaded), then the culprit might be kernel vs driver incompatibility, or leftover old config.

- Check kernel version `uname -r` vs what driver supports. Check the Nvidia website and Ubuntu release notes
- Check if **Secure Boot** is enabled, that can block unsigned modules. If it is enabled, try disabling it temporarily
- Test with older driver versions
