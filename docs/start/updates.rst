.. _updates_section:

Updates
~~~~~~~

The *Imperfect Collection* loader supports easy system updates via USB. This
allows you to apply new features, fixes, or compatibility improvements without
needing to re-etch the entire disk image.

Updating Procedure
-------------------

1. **Prepare the USB Stick**

   - Format a USB stick to **FAT32** if it is not already.
   - Copy your provided update file (e.g., `update.xxxxxxxx.upd`) into the
     **root directory** of the USB stick.

2. **Insert the USB Stick**

   - Insert the USB stick into your MK machine’s USB port.

3. **Verify Update Detection**

   - Access the **Settings menu** by pressing the Service button.
   - Check the **USB Update** status:

     - If it shows **“USB Update: 0”**, the update file has been detected and 
       is ready to install.

4. **Perform the Update**

   - Select the **USB Update** option from the Settings menu.
   - Wait until the USB update is finished and **Do not turn off your MK**.

.. note::

   If the USB Update status remains as **“USB Update: No”**, recheck:

   - The file name (ensure it ends with `.upd` exactly as provided)
   - The USB stick format is FAT32
   - The file is located in the **root directory**, not inside a folder

After updating, your loader will reboot if necessary and incorporate the new 
system changes automatically.

.. note::

   Starting with version **2.0.0**:

   - Update packages are **signed**. A package that was not signed with the
     project's update key is refused, and so is a package whose PMOD content is
     incomplete.
   - The operating system images are not overwritten while they are in use.
     The update stages them next to the old ones (as `<name>.ntdec.new`) and the
     loader swaps them into place **on the next boot**, so the machine may
     reboot once more after the update finishes. Do not turn it off while this
     happens.


Updates reference
^^^^^^^^^^^^^^^^^

All the updates can be downloaded from the following link:
**Updates** `Download here <https://mega.nz/folder/ZUBVhAhZ#-a9nsLkCC9-zY7uSO8apfA>`_

The updates are organized in the following way:

- **1.0.0 - 1.0.1** - `update.9efb5272.upd` (Sat Dec 28 19:41:01 2024 +0900)

  - Fixes a minor issue with the displaying of the license.

- **1.0.1 - 1.0.2** - `update.a353f974.upd` (Sat Dec 28 17:19:48 2024 +0900)

  - Naming of some games changed
  - LUA renaming convention changed

- **1.0.2 - 1.0.3** - `update.17095b2c.upd` (Sun Dec 29 13:51:29 2024 +0900)

   - General graphical fixes to the menu

- **1.0.3 - 1.0.4** - `update.ea12f8f2.upd` (Thu Jan 2 09:28:50 2025 +0900)
  
  - Saves of NXA fixed.
  - Activation of front buttons (both LXIO and PIUIO) for regular navigations.

- **1.0.4 - 1.1.0** - `update.d6e9f412.upd` (Sat May 3 12:17:38 2025 +0900)

  - Introduction of the importer
  - Addition of 2019OS and 2023OS
  - Settings added
  - New bootloader to support the chainload more properly
  - Support for LXIOv2
  - Addition of new drivers for USB handling
  - Games totally removed

- **1.1.0 - 1.1.1** - `update.f7dc69b4.upd` (Sat Jun 28 15:03:50 2025 +0900)

  - New interface
  - General bug-fixes
  - Selection of sound device added
  - New MK3 executables with accurate timing

- **1.1.1 - 1.2.0** - `update.80b87cb9.upd` (Wed Jul 2 20:16:45 2025 +0900)

  - Introduction of all-in-one simulator (PMOD)

- **1.2.0 - 1.2.1** - `update.9dc4253d.upd` (Thu Jul 3 20:09:33 2025 +0900)

  - Putting the Phoenix personal server
  - Putting the Phoenix update definition file
  - Fixes to prex1 and prex2 regarding display issues

- **1.2.1 - 1.3.1** - *file name and date are published with the release in the
  Updates folder.* Summarized from the project history; these changes landed
  between July 2025 and the 1.3.1 build:

  - Support for the newer Phoenix releases.
  - Fixes to the update system (including a USB library fix), and the front
    buttons (USB) are enabled for navigation.
  - 1st and 2nd Dance Floor now use de-compiled versions, and the Rebirth
    problem is fixed.
  - Quieter boot: the first-boot resizing no longer prints its tool output, and
    the FAT resizing is friendlier to big hard disks.
  - **PMOD** standalone release (an image that only contains the simulator),
    with an ext2 variant, and the importer can copy the latest PMOD release.
    PMOD itself moved to **PMOD6**.
  - Executables are now checked against a signature before they are loaded.

- **1.3.1 - 2.0.0** - *file name and date are published with the release in
  the Updates folder.* A new base system; the changes are:

  - **New base OS ("NTDECOS")**: own kernel, initramfs and userland, built
    entirely from source (no original Andamiro payloads are needed to build the
    loader). Graphics are supplied by per-GPU *driver images*, with
    NVIDIA 340.108 / 390.157 ports, a virtio-gpu driver for virtual machines,
    and 720p output taken from the driver. Screen detection now handles
    cloned outputs (XRandR).
  - **Signed boot chain**: grub only boots a signed kernel, and the loader only
    runs signed menu / importer / PMOD files and dm-verity protected OS
    images. See :ref:`security_section`.
  - **Licensing hardening**, with automatic migration of older licenses. See
    :ref:`license_migration_section`.
  - **Menu**: animated, with an *About* screen. Holding TEST no longer breaks
    the menu, the *boot last game* option no longer relaunches a game you just
    quit, and the *Power off* entry works again.
  - **Games**: Phoenix 2.12 boots (and the importer recognizes Phoenix 2.13).
    Prime 2, XX, Prime and Prime Japanese Edition start and stay up. An
    AM.PASS reader emulator and a local game server are included for these
    titles. See :ref:`the games section <games_compat_section>`.
  - Fixes for a heap corruption in the menu (`game.ini` handling) and in the
    sound thread.
  - **PMOD6 images** in vfat, ext2 and NTFS flavors, and ffmpeg 8.0 for PMOD
    (the games keep ffmpeg 4.4.4).
  - The loader image can be built as a qcow2 and run in a virtual machine. See
    :doc:`../dev/building`.
