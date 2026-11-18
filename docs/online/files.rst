.. _online_files_section:

Reference: Where the Files Are
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are two places: the **SETTINGS partition** of the machine's disk and the
**player's USB stick**.

.. _online_files_settings_section:

On the machine (SETTINGS partition)
-----------------------------------

.. list-table::
   :header-rows: 1
   :widths: 44 14 42

   * - File
     - You edit it
     - What it is
   * - ``/SETTINGS/online.ini``
     - Yes
     - Network settings and USB port assignment.
       :ref:`Format <online_online_ini_section>`. Shipped; created with the
       defaults if missing.
   * - ``/SETTINGS/profiles/P1/profile.ini``
     - Yes
     - Default profile of the left side.
       :ref:`Format <online_profile_ini_section>`. Shipped; the menu names it
       after your license; created if missing.
   * - ``/SETTINGS/profiles/P2/profile.ini``
     - Yes
     - Default profile of the right side.
   * - ``/SETTINGS/profiles/P1/save.json`` (and ``P2``)
     - No
     - Scores and totals of that default profile, per game.
   * - ``/SETTINGS/profiles/cards/<card number>/``
     - ``profile.ini`` only
     - The same two files for every real AM.PASS card used on the machine.
       For NX2 to Fiesta 2 and Prime the folder also holds the game's save
       files under their stick names, as if it were the stick
       (:ref:`online_card_profiles_section`).
   * - ``/SETTINGS/F17/ampass.ini``, ``/SETTINGS/F19/ampass.ini``,
       ``/SETTINGS/F23/ampass.ini``
     - Rarely
     - Card reader emulation of Prime 2, XX and Phoenix.
       :ref:`Format <online_ampass_ini_section>`.
   * - ``/SETTINGS/ampass.ini``
     - No
     - Written by the menu. Prime 2, XX and Phoenix do **not** read this
       one, they read their own file above; Prime takes from it the card
       numbers that stand for the two default profiles.
   * - ``/SETTINGS/piu_server.log``
     - No
     - What the game server did during the last game.
       :ref:`How to read it <online_trouble_section>`.
   * - ``/SETTINGS/piuweb/``
     - No
     - Song list and pictures of each installed game, cached for the
       :ref:`Profile manager <online_web_section>`. Encrypted and tied to this
       machine; delete it and it is rebuilt.
   * - ``/SETTINGS/import.key``
     - No
     - The import key of this disk, see :ref:`license_import_section`.

**Shipped with the image.** The image already holds ``online.ini``, both
default ``profile.ini`` files and the ``ampass.ini`` files, with sensible
defaults, so you can open and edit them from the very first boot. The
defaults carry no machine-specific values: the default profiles are named
``PLAYER`` until the menu names them after your license when the machine is
licensed, and the card numbers in ``ampass.ini`` say ``uid=auto`` until the
machine makes its own the first time the file is used (menu or game). Each
one is also **created again when it is missing**: delete a file and the
default comes back the next time it is needed. Machines updated from an
older version do not have the shipped files yet; they get them the same way,
when first needed (first start of Prime, Prime 2, XX or Phoenix, first
license, first start of each game).

**How to reach them.** SETTINGS is the second partition of the disk, in the
ext2 format. Connect the disk to a computer running Linux, or start the
cabinet's computer from a Linux USB stick, and open that partition. Windows
does not read it without extra software. Files changed there are picked up
the next time a game starts.

.. _online_files_stick_section:

On the player's USB stick
-------------------------

.. list-table::
   :header-rows: 1
   :widths: 40 14 46

   * - File
     - You edit it
     - What it is
   * - ``ntdec/profile.ini``
     - Yes
     - Your profile: name, and the avatar you want in each game.
       :ref:`Format <online_profile_ini_section>`.
   * - ``ntdec/save.json``
     - No
     - Your scores in Prime, Prime 2, XX and Phoenix. ``save.json.bak`` is
       the previous version, kept in case of a bad write.
   * - ``prime.bin``
     - No
     - Your identity in Prime (16 bytes). Created for you.
   * - ``nx2save.bin``, ``nx2rank.bin``
     - No
     - NX2's own save.
   * - ``nxasave.bin``, ``nxarank.bin``
     - No
     - NX Absolute's own save.
   * - ``fiesta_save.bin``, ``fiesta_rank.bin``
     - No
     - Fiesta's own save.
   * - ``fiestaex_save.bin``, ``fiestaex_rank.bin``
     - No
     - Fiesta EX's own save.
   * - ``fiesta2_save.bin``, ``fiesta2_rank.bin``
     - No
     - Fiesta 2's own save.

The Profile manager adds to the stick (:ref:`online_web_section`):

.. list-table::
   :header-rows: 1
   :widths: 40 14 46

   * - File
     - You edit it
     - What it is
   * - ``ntdec/pending/<game>.json``
     - No
     - Changes made from the phone that wait for the game to load the save.
   * - ``ntdec/backup/``
     - No
     - The save files as they were before the last change was applied.
   * - ``ntdec/rewards_fiesta.json``, ``ntdec/rewards_fex.json``
     - No
     - PP ledger of Fiesta and Fiesta EX.

The ``.bin`` files sit in the root of the stick, where the games expect them.
They are created the first time the game finds none
(:ref:`online_usb_section`); to start a game's profile over, delete that
game's two files.

A stick is ordinary FAT32: copy the whole ``ntdec`` folder and the ``.bin``
files to keep a backup of a player.
