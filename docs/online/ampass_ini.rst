.. _online_ampass_ini_section:

Reference: ampass.ini
~~~~~~~~~~~~~~~~~~~~~

Prime 2, XX and Phoenix read AM.PASS cards from two card readers. On a machine
without readers the system stands in for them; this file configures that. A
real reader that is plugged in is always used as it is.

**Where:** one file per game, in the game's own folder on SETTINGS
(:ref:`online_files_section`):

.. list-table::
   :header-rows: 1
   :widths: 30 70

   * - Game
     - File
   * - Prime 2
     - ``/SETTINGS/F17/ampass.ini``
   * - XX
     - ``/SETTINGS/F19/ampass.ini``
   * - Phoenix
     - ``/SETTINGS/F23/ampass.ini``

The older games and Prime do not use these files: they take a tapped card from
the real reader directly (:ref:`online_card_profiles_section`).

Each one is shipped with the image and created again with the defaults if it
is missing. You normally never touch it. There is also a ``/SETTINGS/ampass.ini``, written by
the menu: these three games do not read it, so changing it has no effect on
them.

The keys that matter are below; the file holds a few more, to be left as
they are.

.. code-block:: ini

   [AMPASS]
   enabled=1
   readers=2
   insert_on_start=1
   repeat_ms=3000
   bind_readers=1
   [P1]
   uid=04a1b2c3d4e5f6
   [P2]
   uid=04f6e5d4c3b2a1

The shipped file says ``uid=auto`` for both cards, as shown in the table
below, and looks like the example above after the game has started once.

.. list-table::
   :header-rows: 1
   :widths: 22 14 64

   * - Key
     - Default
     - Meaning
   * - ``enabled``
     - ``1``
     - ``0`` turns the emulation off: only real readers.
   * - ``readers``
     - ``2``
     - How many readers to emulate (0-2).
   * - ``repeat_ms``
     - ``3000``
     - Touch the emulated card again every so many milliseconds, as if it
       were left on the reader. This is what logs the default profiles in by
       themselves after a credit. ``0`` = never touch it by itself.
   * - ``insert_on_start``
     - ``1``
     - Touch the card once when the game opens the reader.
   * - ``bind_readers``
     - ``1``
     - Assign reader 1 to player 1 and reader 2 to player 2 while the game
       has none assigned (a machine with fresh settings). ``0`` leaves it to
       the game's *CARD READER* page.
   * - ``[P1]`` / ``[P2]`` ``uid``
     - ``auto``
     - The number of the emulated card of each side. ``auto`` becomes a
       random number the first time the file is used and is kept in the
       file, so every machine has its own. It is what tells the system "this
       is the machine's default profile of that side": do not change it
       unless you know why.

.. note::

   **Machines updated from an older version** already have these files, with
   ``repeat_ms=0``. There, nobody is logged in after a credit unless a real
   card is used. Set ``repeat_ms=3000`` in the file of each game to get the
   behaviour of a new machine.
