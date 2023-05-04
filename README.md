Xploitable modifies your Linux kernel.

## Warning!

Xploitable does not take care of the kernel. After installing a modification,
the system may no longer be bootable. If you can still boot the Linux Kernel after
installing a module, it is possible something is different, that your warranty
is now void (if your PC came with a Linux-based OS), and you are attempting security
loss. If you are worried about a bricked system, do not install Xploitable. **May the force be with you.**

## Install

```bash
bash -c "$(wget -O - https://TylerMS887.github.io/install-xploitable)"
```

`https://TylerMS887.github.io/install-xploitable` is the script downloaded from my GitHub
Pages website.

An AppImage for Xploitable cannot be provided to prevent conflicts with AppImageLauncher
(because the installer could be installed), and that AppImages can bypass some
organization rules.

Snaps for Xploitable cannot be provided because they are sandboxed, and the system's kernel cannot
be accessed by snaps, as there is no Snap connection that offers the kernel.

A package in AUR may be released by someone in the kernel community, as I mainly develop for
Debian-based and Fedora systems.

## Usage

```
xploitable command [-v/--verbose] [-y/--yes/--confirm] [--summary] [...]
```

The options are described at the [wiki](https://github.com/TylerMS887/xploitable/wiki).

> **Warning**: To prevent theft, and keep you safe from hackers, PolicyKit will be triggered
  if you attempt to run Xploitable without root privileges. Either use your password for running
  Xploitable tools or login with the password for `root`.
  
  The `xploitable` command, without root privileges, will not work if you do not have PolicyKit
  installed. Else, you will get this error:
  
  ```
  PolicyKit could not be found. To keep you safe, Xploitable has cancelled the operation.
  
  If you are sure, run this command as root, ideally using sudo.
  If you are in an organization, ask your administrator to run this command.
  Tell them the command.
  
  Command you typed (for reference purpose):
  xploitable command [options]
  
  MAY THE FORCE BE WITH YOU.
  ```

## Built-ins

These modules are available by default on a fresh install:

* Boot `initramfs` from GRUB: Adds `noinit` kernel option to disable the current init system
  and stop the loading sequence after preparing the `initramfs` enviornment (pre-init).
  
  Usage as a GRUB entry:
  ```
  menuentry "Boot to initramfs" {
    linux /boot/<image> -- noinit quiet root=/dev/nvme0n1
    initrd /boot/<initramfs>
    boot
  }
  ```

* `systemd` for `initramfs`: Provides services like backlights during boot. After running `systemd`
  services, an extra service executes in order to run the usual system. Similar to SELinux but without
  security enablement.

* Panic GUI: Show a more graphical error screen with auto-restart when a kernel panic is encountered.

* Distro Logos: Show your distribution's logo. Alternative to the Linux kernel option that shows Tux
  on the screen in non-X TTYs.

* X Programs on Boot: Patches some aspects of Linux to run X11 apps as the init program (for example,
  running a graphical OS installer on boot).

None of these are enabled by default but can be enabled by:

* **For desktop users:** Using the Xploitable Hacker app. It is available if you requested to install it
  during the bootable installer. If not installed, you can install it via `xploitable install-desktop-ui`.

* **For servers and advanced desktop users:** Using the `xploitable` command. To enable a module use
  `xploitable enable`. To do the opposite use `xploitable disable`. `xploitable` is available via your
  system shell or through a desktop, via the `Alt+F2` shortcut.
