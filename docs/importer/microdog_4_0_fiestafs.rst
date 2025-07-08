Microdog 4.0 with FiestaFS-based Importer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Overview
^^^^^^^^

The **Microdog 4.0 with FiestaFS-based Importer** enables installation and
backup of **Pump It Up Fiesta series** games, featuring a specialized FiestaFS
file system format and an advanced update structure.

Credits
^^^^^^^

This importer is made possible thanks to:

- Research of Team HackItUp! alliance
- Update Bank Extractor by H4M573R + Maych1 @ NTDEC

Supported Games
^^^^^^^^^^^^^^^

This importer supports the following titles:

1. **Pump It Up Fiesta 2010** (license: `fiesta`)
2. **Pump It Up Fiesta EX 2011** (license: `fex`)

FiestaFS Details
^^^^^^^^^^^^^^^^

The **FiestaFS file system** uses a compact, concatenated structure:

- The **main filesystem partition** contains single core game file.
- **Update files** are stored **raw after the last partition**, not as 
  traditional partitions themselves.

.. note::
    **Important:**  
    It is **highly advised** to update the game to the **latest available
    update** before performing the backup, ensuring full compatibility and
    feature availability after import.

Installation Procedure
^^^^^^^^^^^^^^^^^^^^^^

Follow these steps to perform an import using the FiestaFS-based Importer:

1. **Launch the importer.**

   - Open the **Settings menu**.
   - Select **The Game Transfer Feature!! (A.K.A Import)**.
   - Choose either **Pump It Up Fiesta 2010** or **Fiesta EX 2011** from the
     list.

2. **Insert the game disk.**

   - Connect the HDD containing the game using either:
     - A **USB-to-SATA converter**
     - A **direct SATA connection**
   - The disk can be inserted **before or after launching** the importer; the 
     system will detect it automatically.

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

   - The dongle is required to extract **license keys** for game activation.
   - If no dongle is present, the importer will fail to copy the required keys.

4. **Begin the import process.**

   The importer will execute the following tasks sequentially:

   - **Retrieve and validate the executable.**
     - The executable is no longer part of the standard OS partition.
     - It is stored in the **raw territory before the first partition**.
     - Two versions may exist; the importer automatically selects the **most
       recent executable**.
     - It checks the version to determine if the game is **fully updated**.

   - **Extract the first BIN file** from the main FiestaFS partition, which
     contains the core game data.

   - **Extract all update BIN files** stored **raw after the last partition**:
     - The importer scans the disk beyond the last partition boundary to locate
       and extract updates.

   - **Extract license keys** using the **Fiesta Updated File Finder (FUFF)**:
     - This involves parsing the **table of contents (TOC)** within FiestaFS to
       locate key data efficiently.

   - **Extract the 100-entry executable table**,  which contains the dongle "OK"
     counter in the settings of the game.

5. **Finish and reboot.**

   - Once the process completes successfully, the system will **automatically
     reboot** to integrate the new game.
   - The newly imported game should appear in the game menu after reboot.

Additional Notes
^^^^^^^^^^^^^^^^

- Ensure that your game disk is updated to the **latest available version** 
  prior to import to avoid compatibility issues.
- For etching compressed disk images (`.img.gz`), tools like **Balena Etcher** 
  handle decompression automatically during writing.
- This importer features specialized handling for FiestaFS’s **non-partitioned
  update storage system**, unique to the Fiesta series architecture.

Troubleshooting
^^^^^^^^^^^^^^^

- **Game not detected:**
  - Verify the HDD or USB drive is properly etched and connected.
  - Confirm updates are applied to the game before import.

- **Dongle not detected:**
  - Ensure the Microdog 4.0 dongle is inserted securely.
  - Try a different USB port if detection fails.

- **Executable version outdated:**
  - Update the game fully before performing the import.

- **Import fails midway:**
  - Re-etch the disk image to eliminate corruption.
  - Check logs for file permission or mounting errors.

- **Game not appearing after reboot:**
  - Retry the import process from the beginning.
  - Confirm that the correct dongle was used for the intended game.
