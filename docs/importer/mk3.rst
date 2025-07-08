Andamiro MK3-based Importer
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Overview
^^^^^^^^

The **Andamiro MK3-based Importer** enables the installation of classic **Pump 
It Up** games originally designed for the MK3 hardware platform. This importer 
works by copying original CD images and preparing them for execution within the 
system.

Credits
^^^^^^^

This importer is made possible thanks to:

- Executables by: TheSchaff
- Code from `bchunk` by Heikki Hannikainen <hessu@hes.iki.fi>
- `cdrtools` for extraction of ISO9660 tracks

About the MK3 Platform
^^^^^^^^^^^^^^^^^^^^^^

The **Andamiro MK3** is a hardware platform used in early Pump It Up arcade 
releases, circa **1999–2003**. MK3 units utilized:

- **Intel Pentium III**
- **PC-based architecture running DOS**
- **Games distributed on CD-ROMs**, sometimes requiring dongles for security
- Early titles featuring **240p-480p VGA output**

CD-based deployment allowed easy distribution of upgrades and new mixes, a 
common arcade practice of the era.

Games Supported
^^^^^^^^^^^^^^^

The importer currently supports the following titles:

1. **Pump It Up The 1st DanceFloor** (license: `1st`)
2. **Pump It Up The 2nd DanceFloor: The Ultimate Remix** (license: `2nd`)
3. **Pump It Up O.B.G: Oldies But Goodies!**  (license: `obg`)
4. **Pump It Up O.B.G: Season Evoluion** (license: `obgse`)
5. **Pump It Up The Collection** (license: `the_collection`)
6. **Pump It Up Perfect Collection** (license: `perfect_collection`)
7. **Pump It Up ExtrA** (license: `extra`)
8. **Pump It Up The Premiere 1** (license: `prem_1`)
9. **Pump It Up The Prex 1** (license: `prex_1`)
10. **Pump It Up The Premiere 2** (license: `prem_2`)
11. **Pump It Up The Rebirth** (license: `rebirth`)
12. **Pump It Up The Prex 2** (license: `prex_2`)
13. **Pump It Up The Premiere 3** (license: `prem_3`)
14. **Pump It Up The Prex 3** (license: `prex_3`)

Each game entry in the importer is mapped to a specific **license name**, which
must have in your license file.

Installation Procedure
^^^^^^^^^^^^^^^^^^^^^^

Follow these steps to install an MK3 game using the importer:

1. **Prepare the USB drive.**

   - Format a USB drive to **FAT32**.
   - Copy the required **BIN/CUE files** of the game to the root directory of
     the USB.

   Below are the **accepted BIN/CUE filenames for each game**:

   - **Pump It Up The 1st DanceFloor**
     - `19990930.BIN` + `19990930.CUE`

   - **Pump It Up The 2nd DanceFloor: The Ultimate Remix**
     - `19991228.BIN` + `19991228.CUE`
     - `20000228.BIN` + `20000228.CUE`

   - **Pump It Up O.B.G: Oldies But Goodies!**
     - `20000508.BIN` + `20000508.CUE`
     - `20000603.BIN` + `20000603.CUE`

   - **Pump It Up O.B.G: Season Evoluion**
     - `20000827.BIN` + `20000827.CUE`
     - *(Note: This version requires only DATA1 and DATA2 during deployment)*

   - **Pump It Up The Collection**
     - `20001114.BIN` + `20001114.CUE`

   - **Pump It Up Perfect Collection**
     - `20001219.BIN` + `20001219.CUE`

   - **Pump It Up ExtrA**
     - `20010209.BIN` + `20010209.CUE`
     - `20010221.BIN` + `20010221.CUE`
     - `010209_1821.BIN` + `010209_1821.CUE`
     - `0102211851.BIN` + `0102211851.CUE`

   - **Pump It Up The Premiere 1**
     - `20010222.BIN` + `20010222.CUE`
     - `20010305.BIN` + `20010305.CUE`

   - **Pump It Up The Prex 1**
     - `20010901.BIN` + `20010901.CUE`

   - **Pump It Up The Premiere 2**
     - `20020311.BIN` + `20020311.CUE`

   - **Pump It Up The Rebirth**
     - `20020311.BIN` + `20020311.CUE`

   - **Pump It Up The Prex 2**
     - `20021014.BIN` + `20021014.CUE`

   - **Pump It Up The Premiere 3**
     - `20030317.BIN` + `20030317.CUE`
     - `20030328.BIN` + `20030328.CUE`

   - **Pump It Up The Prex 3**
     - `20030801.BIN` + `20030801.CUE`
     - `20031014.BIN` + `20031014.CUE`
     - `20030801MK3.BIN` + `20030801MK3.CUE`
     - `20031014MK3.BIN` + `20031014MK3.CUE`


   .. note::
      **Important:**  
      - Filenames may be **case-sensitive**. Make sure to put everything in
        uppercase.
      - Only one valid BIN/CUE pair is needed per game.  
      - Ensure files are **not placed inside folders**, but directly in the root
        of the USB drive.

2. **Launch the importer.**

   - Open the **Settings menu**.
   - Select **The Game Transfer Feature!! (A.K.A Import)**.

3. **Select the desired game** from the list.

4. **Ensure the USB is inserted** when the importer starts.  
   - The importer will detect the BIN/CUE files automatically.
   - It is safe to insert the USB **before or after launching** the importer.

5. **Initiate the import process.**

   The process involves:

   - **Extracting WAV audio tracks** from the CD image.
   - **Extracting ISO filesystem contents** from the data track.
   - **Copying game files to the system’s secure storage**.

6. **Wait for completion.**

   - Do not remove the USB or power off the system during the process.
   - Progress will be displayed on screen.

7. **System reboot.**

   After a successful import, the system will **automatically reboot** to
   finalize installation.

8. **Verify installation.**

   - The new game entry should appear in the main game menu after reboot.
   - If the game does not appear, reattempt the process.

Specific Game Notes
^^^^^^^^^^^^^^^^^^^

- **Pump It Up O.B.G: Season Evoluion (obgse)**  
  Requires only **DATA2** files during deployment (`version 2` in deploy script).

- **Pump It Up The Prex 3 (prex_3)**  
  Modified versions of the BIN/CUE can work, but this importer can only detect
  the canceled songs.

- **Multiple valid CD versions** may exist for a game. Ensure your BIN/CUE
  filenames match one of the listed deployment options.

Troubleshooting
^^^^^^^^^^^^^^^

- **Game not detected:**  
  - Ensure BIN/CUE files are named correctly and placed in the **root of the USB**.
  - Confirm USB is formatted as **FAT32**.

- **Import process fails midway:**  
  - Reformat USB and copy files again.
  - Verify file integrity with checksums if available.

- **Game not appearing after reboot:**  
  - Retry installation.
  - Check for missing security packages or license requirements in the importer
    configuration.
