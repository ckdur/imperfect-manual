Senselock-based Importer
~~~~~~~~~~~~~~~~~~~~~~~~

Overview
^^^^^^^^

The **Senselock-based Importer** enables installation and backup of the latest
generation **Pump It Up Prime 2, XX, and Phoenix series**. These titles utilize
advanced encrypted filesystems and a highly secure dongle protection mechanism.

Supported Games
^^^^^^^^^^^^^^^

This importer supports the following titles:

1. **Pump It Up Prime 2 2018** (license: `prime2`)
2. **Pump It Up XX: 20th Anniversary** (license: `xx`)
3. **Pump It Up Phoenix 2024** (license: `phoenix`)

Filesystem Details
^^^^^^^^^^^^^^^^^^

- **Prime 2** uses **EncryptFS** encryption.
- **XX** and **Phoenix** use **LUKSv1 encryption**.
- Games now store data using a modified version of **AMF**:
  - Files have a `.bin` extension.
  - Two separate strings of updates exist:
    - Theorized purpose: to control asset replacement granularity across updates
      efficiently.

Executable Storage
^^^^^^^^^^^^^^^^^^

- Unlike previous generations:
  - The **executable is not stored in raw disk space**.
  - It is located **inside the encrypted filesystem**.
  - Additionally, it is **encrypted with a dongle-derived key**.

Security Details
^^^^^^^^^^^^^^^^

- Uses **Senselock dongle protection**:
  - Supports **internal execution within the USB device**.
  - ⚠ **Critical warning:**  
    - If **incorrect license requests** are made, the dongle can **self-destruct
      (brick itself)**, permanently rendering the game unusable.

Legal Disclaimer
^^^^^^^^^^^^^^^^

Before initiating the backup process, users are presented with a **mandatory 
legal disclaimer**:

.. code-block:: text

   ************ PLEASE READ *************

   This is a warning message

   This backup uses APIs from Senselock.
   It is known that the dongle COULD BE
   BRICKED, rendering the game useless.
   The creators of this importer DO NOT TAKE
   RESPONSABILITY for a possible bricking
   of your original game. Please proceed
   with caution

   ************ PLEASE READ *************

- Pressing the **red buttons** will indicate **disagreement**, stopping the
  backup process immediately.
- Users must explicitly press center to **agree to proceed**, acknowledging
  that the liability relies on the user.

Installation Procedure
^^^^^^^^^^^^^^^^^^^^^^

Follow these steps to perform an import using the Senselock-based Importer:

1. **Launch the importer.**

   - Open the **Settings menu**.
   - Select **The Game Transfer Feature!! (A.K.A Import)**.
   - Choose the desired game from the supported list above.

2. **Read and agree to the legal disclaimer.**

   - The importer will display a **warning message** outlining potential risks.
   - Press the **confirmation button** to agree and continue.
   - Pressing the **red buttons** disagrees and will cancel the import process
     for safety.

3. **Insert the game disk.**

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

4. **Insert the Senselock dongle.**

   - Required for:
     - **License verification**
     - **Decryption of the executable**

.. note::
    Incorrect dongle usage or corrupted API calls can permanently brick the
    dongle. Proceed with caution.

5. **Begin the import process.**

   The importer will execute the following tasks sequentially:

   - **Mount the encrypted filesystem.**
     - Prime 2: **ext2** + **EncryptFS**
     - XX and Phoenix: **LUKSv1** + **ext2/ext4**

   - **Retrieve and decrypt the executable.**
     - Located within the encrypted filesystem.
     - Decrypted using a **key derived from the Senselock dongle**.

   - **Extract game files and updates:**
     - Main game files are in `.bin` format within the AMF variant.
     - Updates are organized into **two separate update strings** for asset
       replacement control.
     - All data is copied to secure storage for integration.

   - **Extract license keys:**
     - Keys are retrieved using APIs interfacing directly with the Senselock
       dongle.

6. **Finish and reboot.**

   - Upon successful completion, the system will **automatically reboot** to
     integrate the new game.
   - The newly imported game should appear in the game menu after reboot.

Additional Notes
^^^^^^^^^^^^^^^^

- Ensure your game disk is updated to the **latest available version** prior to
  import to maximize compatibility and minimize risk.
- Always **use a stable USB port** and avoid disconnecting devices during the
  import process to prevent bricking.

Troubleshooting
^^^^^^^^^^^^^^^

- **Game not detected:**
  - Verify the HDD or USB drive is properly etched and connected.
  - Confirm updates are applied to the game before import.

- **Dongle not detected or bricked:**
  - Ensure the Senselock dongle is inserted securely.
  - Try a different USB port if detection fails.
  - If bricked, the dongle is permanently unusable and requires manufacturer
    replacement.

- **Executable decryption failure:**
  - Ensure the correct dongle is inserted for the intended game.
  - Retry the import to rule out transient read errors.

- **Import fails midway:**
  - Re-etch the disk image to eliminate corruption.
  - Check logs for filesystem mount or permission errors.

- **Game not appearing after reboot:**
  - Retry the import process from the beginning.
  - Confirm that all extracted files were copied without errors.

- **Check for your dongle:**
  - Check if your original game is running after the backup process.
  - If working, means the dongle still works.

