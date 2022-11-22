Xploitable modifies your Linux kernel.

## Warning!

Xploitable does not take care of the kernel. After installing a modification,
the system may no longer be bootable. If you can still boot the Linux Kernel after
installing a module, it is possible something is different, that your warranty
is now void (if your PC came with a Linux-based OS), and you are attempting security
loss. If you are worried about a bricked system, do not install Xploitable.

## Install

```bash
bash -c "$(wget -O - https://TylerMS887.github.io/install-xploitable)"
```

`https://TylerMS887.github.io/install-xploitable` is the script downloaded from my GitHub
Pages website.

An AppImage for Xploitable cannot be provided to prevent conflicts with AppImageLauncher
(because the installer could be installed), and that AppImages can bypass some
organisation rules.

Snaps for Xploitable cannot be provided because they are sandboxed, and the system's kernel cannot
be accessed by sandboxed packages, as there is no Snap connection that offers the kernel.

A package in AUR may be released by someone in the kernel community, as I mainly develop for
Debian-based and Fedora systems.

## Built-ins

These modules are available by default on an empty install:

* Boot `initramfs` from GRUB: Adds `noinit` kernel option to disable the current init system
  and stop the loading sequence after preparing the `initramfs` enviornment (pre-init).
  
  Usage:
  ```
  menuentry "Boot to initramfs" {
    linux /boot/<image> -- noinit quiet root=/dev/sda1
    initrd /boot/<initramfs>
    boot
  }
  ```

* `systemd` for `initramfs`: Provides services like backlights during boot. After running `systemd`
  services, an extra service executes in order to run the usual system.

* Panic GUI: Show a more graphical error screen with auto-restart when a kernel panic is encountered.

None of these are enabled by default but can be enabled by:

* **For desktop users:** Using the Xploitable Hacker app. It is available if you requested to install it
  during the bootable installer. If not installed, you can install it via `xploitable install-desktop-ui`.

* **For servers and advanced desktop users:** Using the `xploitable` command. To enable a module use
  `xploitable enable`. To do the opposite use `xploitable disable`. `xploitable` is available via your
  system shell or through a desktop, via the `Alt+F2` shortcut.
