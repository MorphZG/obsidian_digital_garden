---
{"dg-publish":true,"permalink":"/01_Reference/stow the dotfiles/","title":"Understanding stow","tags":["linux","utility","configuration"]}
---


# Understanding stow

GNU Stow can be described as a symlink farm manager, it can mirror the structure of one directory into another by creating symbolic links back to the original files.
{ #ef3b67}


This is extremely useful when you have a directory full of configuration files that is managed by git and you want to send all of those configuration files to where they belong in your home directory.

Few important concepts to understand. Can find them in Terminology documentation.

- a package is a folder containing related dotfiles. (vim, bash, git...)
- a stow directory is a folder containing one or more packages.
- target directory is the location in which a package's contents will be symlinked. (usually $HOME directory)

**This is how it looks in practice:**

```sh
target-directory
    stow-directory
        package-1
            .dotfile1
        package-2
            .dotfile2
            .dotfile3

$HOME           --->    (target-directory)
    dotfiles    --->    (stow-directory)
        bash    --->    (package)
            .bashrc     (dotfile)
            .bash_aliases
        git
            .gitconfig
```

> By default stow ignores some files and directories but you can set your own rules by creating the `.stow-local-ignore` file

## Common Use Cases

While still useful for its original purpose, the most popular use for GNU Stow today is managing "dotfiles" – the configuration files that often start with a dot (e.g., `.bashrc`, `.vimrc`) and reside in your home directory. By keeping your dotfiles in a version-controlled directory (like a Git repository), you can easily sync your configurations across multiple machines.

Other uses include:

*   **Managing multiple versions of a program:** You can have different versions of a program in separate directories and use Stow to switch between them by "unstowing" one and "stowing" another.
*   **Organizing project files:** For complex projects, you can use Stow to manage different components or modules, linking them into a central project structure.

## Getting Started

### Installation

GNU Stow is available in the package managers of most Linux distributions and on macOS via Homebrew.

*   **On Debian/Ubuntu-based systems:**

	```bash
    sudo apt install stow
    ```

*   **On Arch Linux:**

	```bash
    sudo pacman -S stow
    ```

*   **On macOS (with Homebrew):**

	```bash
    brew install stow
    ```

### Creating Your Dotfiles Directory

The most common setup involves creating a directory in your home folder to store your dotfiles. A common convention is to name it `.dotfiles`.

```bash
mkdir ~/.dotfiles
cd ~/.dotfiles
```

Inside this directory, you will create subdirectories for each "package" of configuration files you want to manage. For example, you might have separate directories for `bash`, `vim`, and `git`.

A best practice is to keep configurations for different applications in separate packages to make them easier to manage.

## How Stow Works: An Example

Let's say you want to manage your `.bashrc` file.

1.  **Create a package directory:** Inside your `.dotfiles` directory, create a directory for your bash configuration.

	```bash
    mkdir -p ~/.dotfiles/bash
    ```

2.  **Move your configuration file:** Move your `.bashrc` file into this new directory.

	```bash
    mv ~/.bashrc ~/.dotfiles/bash/
    ```

3.  **Stow the package:** From within your `.dotfiles` directory, run the `stow` command.

	```bash
    cd ~/.dotfiles
    stow bash
    ```

Stow will see the `bash` directory and create a symbolic link from `~/.bashrc` to `~/.dotfiles/bash/.bashrc`.

The key principle is that Stow mirrors the directory structure. If a file needs to be in a subdirectory of your home directory, you must replicate that structure within your package directory. For example, if you have a configuration file at `~/.config/nvim/init.vim`, your Stow package structure would look like this:

```
~/.dotfiles/nvim/.config/nvim/init.vim
```

When you run `stow nvim` from `~/.dotfiles`, Stow will create the necessary directories and symlinks.

## Essential Stow Commands

*   `stow <package>`: Creates the symbolic links for the specified package.
*   `stow -D <package>` or `stow --delete <package>`: Removes the symbolic links for the specified package.
*   `stow -R <package>` or `stow --restow <package>`: "Restows" a package, which is useful for updating links after you've made changes. It will first delete the existing links and then create new ones.
*   `stow .`: This is a convenient way to stow all packages within the current directory.

## Using Stow with Git

The real power of this approach comes when you combine it with Git.

1.  **Initialize a Git repository:** In your `.dotfiles` directory, initialize a new Git repository.

	```bash
    cd ~/.dotfiles
    git init
    ```

2.  **Add and commit your files:**

	```bash
    git add .
    git commit -m "Initial commit of my dotfiles"
    ```

3.  **Push to a remote repository:** You can then push your dotfiles to a platform like GitHub or GitLab. This serves as a backup and allows you to easily clone your dotfiles onto a new machine.

When you set up a new machine, you can simply clone your `.dotfiles` repository and then use `stow` to create all the necessary symbolic links.

## Ignoring Files

Stow will ignore certain files by default, such as `.git`. You can create a `.stow-local-ignore` file in your stow directory to specify additional files or patterns that you don't want Stow to manage.

## read more

- [systemcrafters.net/blogpost](https://systemcrafters.net/managing-your-dotfiles/using-gnu-stow/) "Using GNU Stow to manage symbolic links"
- [willhbr.net/blogpost](https://willhbr.net/2024/03/06/tmux-conf-with-commentary/) - "tmux.conf, With Commentary"
- [gnu.org/manual](https://www.gnu.org/software/stow/manual/) GNU stow manual
- [youtube.com/video](https://www.youtube.com/watch?v=y6XCebnB9gs) "Stow has forever changed the way i manage my dotfiles" by Dreams of autonomy
- [youtube.com/video](https://www.youtube.com/watch?v=FHuwzbpTTo0) "Manage your dotfiles like a superhero" by Jake Wiesler
- [jakewiesler.com/blogpost](https://www.jakewiesler.com/blog/managing-dotfiles) Understanding stow
- [youtube.com/video](https://www.youtube.com/watch?v=CFzEuBGPPPg) "Sync your .dotfiles with git and GNU Stow like a pro" by DevInsideYou
- [youtube.com/video](https://www.youtube.com/watch?v=CxAT1u8G7is) "Give your dotfiles a home with GNU stow" by System crafters
