PMOD Song & SongPackage Importer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Overview
^^^^^^^^

The **PMOD Importer** enables the integration of external songs and song
packages into **PMOD**, a **StepMania-based simulator** included within
Imperfect Collection that utilizes the original assets from imported Pump It Up
games for the songs.

PMOD Functionality
^^^^^^^^^^^^^^^^^^

- **Automatically detects imported games:**
  - All songs from supported imported games are **automatically added** to the
    PMOD song wheel upon boot.

.. note::
    Songs from the following games **cannot be detected by PMOD** due to
    compatibility limitations:
    - **1st dance floor**
    - **2nd dance floor**
    - **3rd dance floor - OBG**
    - **Extra**

Supported External Song Formats
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Besides importing assets from other games, PMOD supports the addition of 
**custom songs and song packages**.

### Song Import Requirements

1. **USB Drive:**
   - Format: **FAT32**
   - Folder structure:
     - Place all songs inside a folder named **`Songs`** in the root of the USB.

2. **Song Folder Structure:**

   The structure should follow standard **StepMania / PumpSanity / StepP1**
   conventions, as shown:

   .. code::
        /Songs/
        ├── Group Name 1/
        │ ├── Song A Folder/
        │ │ ├── SongA.sm
        │ │ ├── SongA.ogg
        │ │ └── additional files...
        │ └── Song B Folder/
        │ ├── SongB.sm
        │ └── SongB.ogg
        └── Group Name 2/
        └── Song C Folder/
        ├── SongC.sm
        └── SongC.mp3

- **Group folders** organize songs by category or theme.
- Each **individual song folder** must contain:
  - A **chart file** (`.sm`, `.ssc`, etc.).
  - **Audio files** (`.ogg`, `.mp3`, etc.).
  - Optional background images, banners, or videos.

3. **Song Packages:**
- Supported in **ZIP format**.
- Place these files in a folder named **`SongPackages`** in the root of the USB.

Usage Instructions
^^^^^^^^^^^^^^^^^^

Follow these steps to import songs or song packages into PMOD:

1. **Prepare your USB drive.**

- Format the USB as **FAT32**.
- Create a **`Songs` folder** and/or **`SongPackages` folder** in the root
  directory.
- Copy your songs and packages into their respective folders as per the
  structure above.

2. **Insert the USB drive.**

- Plug the USB drive into your Imperfect Collection system.

3. **Launch the importer.**

- Open the **Settings menu**.
- Select **The Game Transfer Feature!! (A.K.A Import)**.
- Choose **PMod Song Importer/Deleter** from the list.

4. **Select import mode.**

The importer will provide options:

- **Copy all songs from `Songs` and `SongPackages` folders**
- **Delete existing imported songs**

5. **Complete the process.**

- If **copying**, the importer will begin transferring all detected songs or
  packages to the internal PMOD filesystem.
- If **deleting**, it will remove existing imported packages accordingly.

6. **Reboot the system.**

- After completion, the system will **automatically reboot**.
- Newly imported songs and packages will be available in the **PMOD song wheel**.

Additional Notes
^^^^^^^^^^^^^^^^

- **Free license limitations:**  
Importing external songs doesn't require any license. But, still would be nice
if you support us. Please visit the patreon for more information

**[Imperfect Collection Patreon](https://www.patreon.com/ckdur)**

- Ensure all `.sm` or `.ssc` chart files are properly formatted for
  compatibility with PMOD.

Troubleshooting
^^^^^^^^^^^^^^^

- **Songs not detected:**
- Verify folder and file structure matches StepMania conventions.
- Confirm USB is FAT32 and readable by the system.

- **Packages not detected:**
- Ensure ZIP files are not nested within additional folders inside 
  **`SongPackages`**.

- **Corrupted files after import:**
- Recheck encoding and compatibility of audio files and chart definitions before
  re-importing.

- **PMOD not appearing in importer menu:**
- Ensure your Imperfect Collection version supports PMOD integration.
