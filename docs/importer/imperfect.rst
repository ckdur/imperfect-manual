Imperfect Importer
~~~~~~~~~~~~~~~~~~

Overview
^^^^^^^^

The **Other Games Importer** allows users to **transfer games directly between
two Imperfect Collection installations**. This feature is particularly useful
for setting up multiple systems efficiently without needing to repeat individual
disk-based imports for each game.

Licensing Requirements
^^^^^^^^^^^^^^^^^^^^^^

.. warning::

   **EXPERIMENTAL.** The transfer between two disks of 2.0.0 was written and
   checked with automatic tests, but it has not been run end to end on real
   disks yet. Keep the original games and a backup of the source disk, and
   expect the messages on the screen to differ from this page in details.

**Both** machines must hold a **paid** license:

- **The machine that receives** the games must have a full (non-free) license.
- **The disk that is the source** must also have a full license of its own.
- A **free** license, or a license that was **migrated** from an older version,
  cannot send or receive games.
- The source must be a disk of **2.0.0 or later and of the same release** as
  the machine that receives (a release disk reads release disks, a debug disk
  reads debug disks). If the source is older or newer, the screen asks you to
  **update the older one** first. Disks of 1.3.x cannot be a source any more.
- A game is copied only if the license of the receiving machine has that game
  (for example a license without Phoenix skips Phoenix and goes on with the
  rest).

Why? We do not support piracy.

For information on upgrading to a full license, visit:

**[Imperfect Collection Patreon](https://www.patreon.com/ckdur)**

Feature Description
^^^^^^^^^^^^^^^^^^^

The Other Games Importer enables:

- **Direct transfer of games** from one Imperfect Collection installation to
  another. The source disk is connected to the receiving machine as a second
  disk (USB or SATA) **after** the receiving machine has started, and is only
  **read**.

- **Two operational modes:**

  - Copy **only the currently selected game**.
  - Copy **all available games** from the source system.

Usage Instructions
^^^^^^^^^^^^^^^^^^

1. **Boot into Imperfect Collection.**

   - Ensure the machine has a **full (non-free) license**, and so does the
     source disk.

2. **Connect the source Imperfect Collection system.**

   - Use the appropriate connection interface to link both systems.
   - The importer will automatically detect the connected Imperfect Collection
     containing the games to copy.

3. **Navigate to the settings menu.**

   - Open the **Settings**.
   - Select **The Game Transfer Feature!! (A.K.A Import)**.

4. **Choose the desired game.**

   - Select **any game** from the settings menu list.

5. **Select transfer mode when prompted.**

   - If another Imperfect Collection is detected, you will be asked:

     - **“Copy only this game?”** (Red buttons)

       - Select to transfer **only the selected game**.

     - **“Copy all games?”** (Center button)

       - Select to transfer **all available games** from the connected source.

6. **Begin the transfer process.**

   - The importer will copy the selected game(s) from the connected Imperfect
     Collection to your system.

   - Progress will be displayed on screen.

7. **Wait for completion and reboot.**

   - After the transfer is complete, the system will **reboot automatically**.
   - All copied games will appear in the game menu.

Troubleshooting
^^^^^^^^^^^^^^^

- **No source system detected:**

  - Ensure the Imperfect Collection system is connected properly. Connect it
    **after** the destinated Imperfect Collection already booted.

  - Verify cable integrity and connection interface compatibility.

- **Feature unavailable, or the screen says the license or the disk is not
  accepted:**

  - Confirm that **both** disks have a **full license** (not a free or migrated
    one) and are of the same 2.0.0 release.
  - Visit **[https://www.patreon.com/ckdur](https://www.patreon.com/ckdur)** to
    upgrade if needed.

- **Transfer fails midway:**

  - Reconnect both systems and retry the transfer.
  - Check storage space availability on the target system.

Additional Notes
^^^^^^^^^^^^^^^^

- The games are copied exactly as they are. **Saves, profiles, credits and the
  license are never copied**: every machine keeps its own.
- A game that is already installed asks before it is replaced, and nothing is
  written when the disk has not enough free space.
- If the power goes off during the copy, run it again: the half-copied game is
  cleaned up and the menu does not start a half game.
- This feature significantly reduces deployment times when **multiple systems
  require identical game sets**.

- Always ensure the **source system has verified working games** before
  initiating the transfer to avoid propagating corrupted data.
