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

- **1.2.0 - 1.2.1** - `update.9dc4253d.upd` (Wed Jul 3 20:16:45 2025 +0900)

  - Putting the Phoenix personal server
  - Putting the Phoenix update definition file
  - Fixes to prex1 and prex2 regarding display issues
