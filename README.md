Xploitable modifies your Linux kernel.

If you thought it was impossible, it's actually easy! Pull up your terminal,
download an Xploitable modification, and open it.

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

An AppImage for Xploitable cannot be provided to prevent conflicts with the `ace` image
launcher, and that AppImages can bypass some organisation rules.

A Snap or Flatpak cannot be provided because they are sandboxed, and the kernel cannot be
accessed by sandboxed packages.

A package for AUR may be released by someone in the kernel community. Possibly the same
for a PPA (Debian/Ubuntu/Kali/KDE Neon/etc.) and a Copr repository (Red Hat/Fedora/etc.).

## Built-In Modules

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

* Panic GUI: Show a more graphical error screen when a kernel panic is encountered.
