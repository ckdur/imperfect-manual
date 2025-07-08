Infinity-based Importer
~~~~~~~~~~~~~~~~~~~~~~~

Overview
^^^^^^^^

The **Infinity-based Importer** enables installation and backup of the unique
**Pump It Up Infinity** title, a side series in the Pump It Up franchise 
featuring an Stepmania-based engine.

Supported Games
^^^^^^^^^^^^^^^

This importer supports:

- **Pump It Up Infinity** (license: `infinity`)

Game Details
^^^^^^^^^^^^

- **Pump It Up Infinity** is a **side series project**, created as an **SM-based
  adaptation** within the franchise.

  *"Made with Love"*

Security Details
^^^^^^^^^^^^^^^^

- Uses **Microdog 4.0 dongle protection**:
  - Required only at **boot time** for license validation.
- **Executable encryption**:
  - The game executable is encrypted using a **dongle-derived key**.
  - Due to implementation oversights, the encryption key can be **bruteforced**.

Filesystem Details
^^^^^^^^^^^^^^^^^^

- Utilizes the **XFS (X File System)**:
  - This is **unique within Pump It Up titles**.
  - The importer includes a **custom XFS extraction tool**, implemented using
    components from **xfsprogs**.

.. note::
    Developing support for the XFS filesystem required **significant engineering
    effort**, as XFS is a powerful Linux filesystem not natively supported by
    traditional importer workflows. Full compatibility was achieved through
    **custom adaptation of libxfs and extraction utilities**.

Encrypted Assets
^^^^^^^^^^^^^^^^

Game assets are stored as **encrypted ZIP files**, divided into two types:

1. **Pre-1.07 assets:**
   - Contain their own **embedded decryption key**.
   - Can be used **without dongle presence**.

2. **Post-1.07 assets:**
   - Require a **key transformation process**:
     - Uses the **head and tail segments of the dongle key** to derive the final
       decryption key.
   - Dongle presence is **mandatory** to decrypt these files.

Installation Procedure
^^^^^^^^^^^^^^^^^^^^^^

Follow these steps to perform an import using the Infinity-based Importer:

1. **Launch the importer.**

   - Open the **Settings menu**.
   - Select **The Game Transfer Feature!! (A.K.A Import)**.
   - Choose **Pump It Up Infinity** from the list.

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

   - Required to:
     - **Decrypt the executable** using the dongle-derived key.
     - **Extract the keys** for post-1.07 assets.

4. **Begin the import process.**

   The importer executes the following tasks sequentially:

   - **Retrieve the encrypted executable** from the raw disk region.
   - **Decrypt the executable** using the dongle-derived key or bruteforce
     fallback.
   - **Mount and parse the XFS filesystem** using the importer’s custom XFS
     extraction tool.
   - **Extract all encrypted ZIP assets:**
     - Pre-1.07 assets are decrypted using embedded keys.
     - Post-1.07 assets require dongle-based key transformation for decryption.

5. **Finish and reboot.**

   - Upon successful completion, the system will **automatically reboot** to
     integrate the new game.
   - The newly imported game should appear in the game menu after reboot.

Implementation Effort
^^^^^^^^^^^^^^^^^^^^^

**Special emphasis:**  

Supporting **Pump It Up Infinity** required **dedicated development of an
internal XFS extraction tool**, integrating **xfsprogs-based implementations**
for compatibility. This represents one of the **most technically demanding
importers** within the Pump It Up franchise due to its **non-standard filesystem
and mixed encryption schemes**.

Troubleshooting
^^^^^^^^^^^^^^^

- **Game not detected:**
  - Verify the HDD or USB drive is properly etched and connected.
  - Confirm updates are applied to the game before import.

- **Dongle not detected:**
  - Ensure the Microdog 4.0 dongle is inserted securely.
  - Try a different USB port if detection fails.

- **Executable decryption failure:**
  - Retry using dongle-derived decryption.
  - If issues persist, confirm dongle integrity or attempt bruteforce fallback cautiously.

- **XFS extraction failure:**
  - Re-etch the disk image to eliminate corruption.

- **Game not appearing after reboot:**
  - Retry the import process from the beginning.
  - Confirm all assets were decrypted and copied successfully.
