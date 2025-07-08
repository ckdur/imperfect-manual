Microdog 4.0 regular-based Importer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Overview
^^^^^^^^

The **Microdog 4.0 regular-based Importer** enables installation and backup of later-generation Pump It Up titles, particularly the **NX2 and NXA series**. This importer manages disk imaging, file extraction, and license key retrieval using the updated Microdog 4.0 dongle system.

Credits
^^^^^^^

This importer is made possible thanks to:

- Research of Team HackItUp! alliance

Supported Games
^^^^^^^^^^^^^^^

The following games are supported under this importer:

1. **Pump It Up NX2: Next Xenesis** (license: `nx2`)
2. **Pump It Up LongFei Feng Wu (NX2 China)** (license: `nx2_cn`)
3. **Pump It Up NXA: NX Absolute** (license: `nxa`)
4. **Pump It Up Xin ShiJi Wu Zhe (NXA China)** (license: `nxa_cn`)

Installation Procedure
^^^^^^^^^^^^^^^^^^^^^^

Follow these steps to perform an import using the Microdog 4.0 regular-based Importer:

1. **Launch the importer.**

   - Open the **Settings menu**.
   - Select **The Game Transfer Feature!! (A.K.A Import)**.
   - Choose the desired game from the supported list above.

2. **Insert the game disk.**

   - Connect the HDD containing the game using either:
     - A **USB-to-SATA converter**
     - A **direct SATA connection**
   - The disk can be inserted **before or after launching** the importer; the system will detect it automatically.

   .. note::
        Any **valid disk image etched into an HDD or USB drive** will work, 
        regardless of its serial number. You can etch a disk image backup you
        have. This is due to these games being so old, that probably are not
        functional.

        **Etching a disk image:**

        - If you have a game `.img` or compressed `.img.gz` file:
            - Use tools like **Balena Etcher** or **Rufus** to write the image
              to your HDD or USB drive.
            - Ensure the writing process completes without errors to avoid read
              issues during import.

3. **Insert the Microdog 4.0 dongle.**

   - The dongle is required to extract **license keys** necessary for game
     activation.
   - If no dongle is present, the importer will fail to copy the required keys.

4. **Wait for the backup process to complete.**

   The importer will perform the following tasks sequentially:

   - **Mounting the disk** to access its filesystem.
   - **Copying all game files** to secure storage.
   - **Retrieving the main executable** for launch configuration.
   - **Extracting license keys** from game data files, including:
     - `DAT`
     - `AUD`
     - `PNZ`
     - `MOV`
   - **Parsing and backing up the 100-entry executable table**, which contains
     the dongle "OK" counter in the settings of the game.

5. **Finish and reboot.**

   - Once the process completes successfully, the system will **automatically
     reboot** to integrate the new game.
   - The newly imported game should appear in the game menu after reboot.

Additional Notes
----------------

- This process is **identical to the Microdog 3.4-based importer**, except it
  uses the **Microdog 4.0 dongle extractor** instead. Involves a different
  protocol which the user usually is unaware of.
- The importer supports **multiple image versions or disk revisions**, as long
  as the data structure remains compatible with Microdog 4.0 protection.
- Ensure **both the disk and dongle are functional** to avoid incomplete backups.
- For etching compressed images (`.img.gz`), tools like **Balena Etcher** handle
  decompression automatically during writing.

Troubleshooting
---------------

- **Game not detected:**
  - Verify the HDD or USB drive is properly etched and connected.
  - Check USB-to-SATA converters for sufficient power delivery.

- **Dongle not detected:**
  - Ensure the Microdog 4.0 dongle is inserted securely.
  - Try a different USB port if detection fails.

- **Import fails midway:**
  - Re-etch the image to eliminate potential corruption.
  - Check logs for file permission or mounting errors.

- **Game not appearing after reboot:**
  - Retry the import process from the beginning.
  - Confirm that the correct dongle was used for the intended game.
