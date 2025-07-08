.. _importer_section:

The Game Transfer Feature (Importer)
------------------------------------

The Game Transfer Feature (Importer) is an all-in-one back up utility to import
the games.

The Importer utility, also known as **"The Game Transfer Feature!! 
(A.K.A Import)"**, allows users to install new games into the system directly
from the settings menu.

Overview
^^^^^^^^

This feature simplifies the process of transferring games by guiding the user
through disk and dongle detection, game copying, and system update steps.

Typical Procedure
^^^^^^^^^^^^^^^^^

To use the Importer, follow these steps:

1. **Open the settings menu.** More info can be found in :ref:`settings_section`
section.

2. **Select the option:** Go down to the **"The Game Transfer Feature!! 
(A.K.A Import)"**.

3. **Browse the list of installable games.**

A list containing all available games that can be installed will appear on the
screen.

4. **Select the desired game.**

Remember to connect the game original disk. (SATA to USB, and SATA-only are ok).
If the game has a dongle, connect that also.

5. **Importer screen activation.**

The Importer will start and attempt to **detect required disks and dongles**
for the selected game.

.. note::

   The importer may not detect the games right away. You can retry as many times
   as you want stepping in the "center" button. To abort, just step on "red".

.. warning::

   Sometimes the importer screen appears small. This is due to the monitor/TV
   you attached. Unfortunately, the detection of the DPI is not complete in the
   original OS. If there is a fix for this, it will be fixed as soon as
   possible.

6. **Insert the required disk or dongle.**

- If the disk is detected successfully, the system will begin with **the backup
  of game data** automatically.

7. **Wait for the process to finish.**

- The copying process may take some time depending on the game size.
- Do not interrupt power or eject media during the operation.

8. **System reboot.**

Once the installation is complete, the system will **automatically reboot** to
finalize the setup.

9. **Verify the game installation.**

After rebooting, the newly installed game should appear as a new entry in the
main menu.

Notes
^^^^^

- Each game may have **unique installation requirements or detection methods**.
  Always follow any specific prompts displayed on the Importer screen. Specifics
  of the installation will be explained in further sections.
- Ensure disks and dongles are **clean and properly connected** to avoid
  installation failures. Failures on the SATA cable or poor USB connection can
  interrupt the process.
- If a game fails to install, retry the process from the beginning.

Specifics
^^^^^^^^^

The specifics for each type of game are written in the following sections.
If there are some troubles in your installation process, please refer to the 
specifics of each game type.

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   mk3
   microdog_3_4
   microdog_4_0_single
   microdog_4_0_fiestafs
   infinity
   hasp
   senselock
   pmod
   other
