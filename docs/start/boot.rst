Inserting the Disk and Booting
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Once you have etched the *Imperfect Collection* image onto your hard disk, you 
are ready to install it into your MK machine and begin the boot process.

Understanding the MK Hardware
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The MK is essentially a standard PC with specialized *Pump It Up* hardware
components. Installing the loader is similar to installing a hard disk in any
desktop PC.

Connecting the Disk
^^^^^^^^^^^^^^^^^^^

Power off your MK completely and disconnect it from its power source. After that,
just connect your etched disk into any available SATA slot. After you power on,
you should be able to see later the booting process of the *Imperfect Collection*.
You can jump directly to the section :ref:`booting_into` section.

Connecting the Disk alongside another original Pump It Up game
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you plan to use the *Imperfect Collection* alongside an original Pump It Up
game disk, it is important to connect the disks in the correct order.

1. **Power off your MK completely** and disconnect it from its power source.
2. Open the MK cover to access the internal SATA ports and hard disk connections.
3. Identify the SATA ports on the motherboard. They are usually numbered 
   sequentially (e.g., SATA0, SATA1, SATA2, …).

   - **Connect the original Pump It Up game disk to the SATA port with the lowest number** (for example, SATA0).  
   - **Connect the Imperfect Collection disk to a higher-numbered SATA port** (for example, SATA1 or SATA2).

This ensures that the original game disk is recognized as `/dev/sda` and the
*Imperfect Collection* disk as `/dev/sdb` during boot.

.. _booting_into:

Booting into Imperfect Collection
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

After connecting the disk(s):

1. Reassemble your MK and reconnect the power.
2. Power on the machine and enter the BIOS setup. This usually involves pressing
   the **DEL**, **F2**, or **F12** key immediately after turning on the system.
   The exact key will appear on-screen during startup.
3. In the BIOS, navigate to the **Boot** settings.
4. **Change the boot priority to select the Imperfect Collection disk**, to the
   disk connected to the higher-numbered SATA port.
5. Save and exit the BIOS.

Some newer motherboards and MK systems boot by default in **UEFI mode**, which
may prevent the *Imperfect Collection* disk (formatted as an MBR bootable image)
from starting correctly. In these cases, you need to configure the BIOS to boot
in **Legacy BIOS mode** or enable **CSM (Compatibility Support Module)**.

Follow these steps if your MK does not boot from the Imperfect Collection disk:

1. **Enter BIOS Setup**

   - Power on the MK and immediately press the **DEL**, **F2**, or **F12** key 
     (depending on your motherboard) to enter the BIOS setup utility.

2. **Locate Boot Mode Settings**

   - Look for settings under tabs such as **Boot**, **Advanced**, or **Startup**.
   - Find the **Boot Mode**, **UEFI/Legacy Boot**, or **CSM Support** option.
     The exact naming varies by motherboard manufacturer.

3. **Enable Legacy Boot or CSM Mode**

   - If your BIOS has a **Boot Mode** option:
     
     - Change it from **UEFI** to **Legacy** or **Both (UEFI + Legacy)** if 
       available.  
   
   - If your BIOS has **CSM Support**:

     - Enable **CSM (Compatibility Support Module)**.  
     - Within CSM settings, ensure **Boot Device Control** or **Boot from 
       Storage Devices** is set to **Legacy Only** or **UEFI and Legacy**.

4. **Adjust Boot Priority**

   - After enabling Legacy Boot or CSM, ensure the Imperfect Collection disk
     remains selected as the first boot device.

5. **Save and Exit**

   - Save your changes (usually **F10**) and exit the BIOS. The system will
     reboot.

After these adjustments, your MK should boot correctly from the *Imperfect
Collection* disk using MBR mode.

.. note::

   If you continue to experience boot issues, verify that:

   - The disk was etched properly.
   - SATA cables and power connectors are firmly attached.
   - No Secure Boot option is enabled, as it may block unsigned MBR bootloaders.

What to Expect
^^^^^^^^^^^^^^

After booting, you should see the Imperfect Collection bootloader displayed on
screen. From here, some additional resizing steps will happen:

- **The resizing of the base partition**. You notice this with the message `First boot. Resizing...`
  in the boot screen. This process takes some seconds, and will reboot the MK.
- **Filesystem expansion**. This is the second resizing. Will use the previously
  available space to expand the filesystem where all the games will be installed.

.. note::

   If the steps above failed, you can try:

   - Etching the disk again.
   - If the disk was already etched with important information, you can delete
     `.first` and `.second` from the `SETTINGS` partition (linux only).


^^^^^


After booting and resizing, you should see the Imperfect Collection menu 
displayed on screen. From here, you can proceed to license the loader, install 
and select games, or perform any additional configurations provided by the
loader.

Proceed to the next section to learn about navigating the loader menu and accessing its features.
