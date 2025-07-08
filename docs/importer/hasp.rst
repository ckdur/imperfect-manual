Hasp-based Importer
~~~~~~~~~~~~~~~~~~~

Overview
^^^^^^^^

The **Hasp-based Importer** enables installation and backup of later-generation
**Pump It Up Fiesta 2 and Prime series** games, protected using **HaspHL dongle
security**. These games introduce the new **AMF (Andamiro Filesystem)** format
with restructured executable and update storage.

Credits
^^^^^^^

This importer is made possible thanks to:

- Codes by Team HackItUp! and HUEBR teams.

Supported Games
^^^^^^^^^^^^^^^

This importer supports the following titles:

1. **Pump It Up Fiesta 2 2013** (license: `f2`)
2. **Pump It Up Prime 2015** (license: `prime`)
3. **Pump It Up Prime 2015 (Japanese Edition)** (license: `prime_je`)

Filesystem Details
^^^^^^^^^^^^^^^^^^

- Games now use the **AMF (Andamiro Filesystem)** format:
  - **Main game files and updates** are stored inside the game folder in
    sequential number order.
- **Executables (EXEs)** are stored in the **raw territory before the first
  partition**:
  - Two versions may exist; the importer automatically selects the **most recent
    executable** to ensure the game is updated.

Security Details
^^^^^^^^^^^^^^^^

- Uses **HaspHL dongle protection**.
- **Key extraction** is performed via **patched game executable**:
  - During extraction, the game screen will appear with a **counter indicating
    progress**.
- **100-entry executable table no longer exists** in this generation:
  - Game license validation is solely through **dongle presence**.

✔ **Prime-specific note:**
- For **Prime** and **Prime Japanese Edition**, the **executable is encrypted**
  using a **key derived from the dongle**. The importer manages the decryption
  with a fixed key. Please make sure you have 1.22 or 1.21 versions.

Installation Procedure
^^^^^^^^^^^^^^^^^^^^^^

Follow these steps to perform an import using the Hasp-based Importer:

1. **Launch the importer.**

   - Open the **Settings menu**.
   - Select **The Game Transfer Feature!! (A.K.A Import)**.
   - Choose the desired game from the supported list above.

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

3. **Insert the HaspHL dongle.**

   - The dongle is required to extract license keys for asset decryption.
   - If no dongle is present, the importer will fail to proceed.

4. **Begin the import process.**

   The importer performs the following tasks sequentially:

   - **Retrieve and validate the executable.**
     - Located in the **raw territory before the first partition**.
     - If multiple versions exist, the **most recent version** is used for
       import validation.

   - **Extract game files and updates:**
     - Files are stored inside the AMF game folder in sequential order.
     - The importer copies all main and update files to secure storage.

   - **Extract license keys via executable patching:**
     - The importer patches the executable to interface with the dongle and
       extract keys.
     - The game screen will appear with a **progress counter** during this
       process.

5. **Finish and reboot.**

   - Upon successful completion, the system will **automatically reboot** to
     integrate the new game.
   - The newly imported game should appear in the game menu after reboot.

Additional Notes
^^^^^^^^^^^^^^^^

- Ensure that your game disk is updated to the **latest available version** 
  prior to import for compatibility.
- For etching compressed disk images (`.img.gz`), tools like **Balena Etcher** 
  handle decompression automatically during writing.
- The importer supports **Prime and Prime JE encrypted executables**, handling
  decryption automatically using the dongle-derived key.

Troubleshooting
^^^^^^^^^^^^^^^

- **Game not detected:**
  - Verify the HDD or USB drive is properly etched and connected.
  - Confirm updates are applied to the game before import.

- **Dongle not detected:**
  - Ensure the HaspHL dongle is inserted securely.
  - Try a different USB port if detection fails.

- **Executable version outdated:**
  - Update the game fully before performing the import.

- **Import fails midway:**
  - Re-etch the disk image to eliminate corruption.
  - Check logs for file permission or mounting errors.

- **Game not appearing after reboot:**
  - Retry the import process from the beginning.
  - Confirm that the correct dongle was used for the intended game.
