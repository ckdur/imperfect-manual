.. _online_profile_ini_section:

Reference: profile.ini
~~~~~~~~~~~~~~~~~~~~~~

**Where:** ``<USB stick>/ntdec/profile.ini`` for a player,
``/SETTINGS/profiles/P1/profile.ini`` and ``P2`` for the machine's default
profiles (:ref:`online_files_section`).

A plain text file made of sections. Lines starting with ``;`` are comments.

.. code-block:: ini

   [profile]
   name=CKDUR

   [phoenix]
   avatar=17
   country=47

   [xx]
   avatar=80
   title=5

   [prime2]
   avatar=3

   [prime]
   avatar=3

   [nx2]
   avatar=5

   [nxa]
   avatar=5

   [fiesta]
   avatar=6

   [fex]
   avatar=6

   [fiesta2]
   avatar=6

The ``[profile]`` section
-------------------------

.. list-table::
   :header-rows: 1
   :widths: 16 84

   * - Key
     - Meaning
   * - ``name``
     - Your name in every game. Letters ``A-Z`` and digits; up to 12
       characters. Only Phoenix uses all 12: NX2 and NX Absolute use the
       first 8, the other games the first 11.

The game sections
-----------------

One section per game; every key is optional. A value you leave out gets a
default. For the avatar that is a random one, chosen once and then kept, in
Prime, Prime 2, XX and Phoenix, and the first picture (0) in the older
games; a number outside the game's range also becomes 0 there.

.. list-table::
   :header-rows: 1
   :widths: 16 20 16 48

   * - Section
     - Game
     - Key
     - Values
   * - ``[phoenix]``
     - Phoenix
     - ``avatar``
     - 0-164
   * -
     -
     - ``country``
     - 0-247: the flag next to your name (0 = none)
   * - ``[xx]``
     - XX
     - ``avatar``
     - 69-163
   * -
     -
     - ``title``
     - 0-199: the title above your name (109 = none)
   * - ``[prime2]``
     - Prime 2
     - ``avatar``
     - 0-39
   * - ``[prime]``
     - Prime
     - ``avatar``
     - 0-39
   * - ``[nx2]``
     - NX2
     - ``avatar``
     - 0-127
   * - ``[nxa]``
     - NX Absolute
     - ``avatar``
     - 0-163
   * - ``[fiesta]``
     - Fiesta
     - ``avatar``
     - 0-214
   * - ``[fex]``
     - Fiesta EX
     - ``avatar``
     - 0-234
   * - ``[fiesta2]``
     - Fiesta 2
     - ``avatar``
     - 0-259
   * - any of them
     -
     - ``name``
     - Replaces the name of ``[profile]`` in that game only

The numbers are the game's own: the avatar number is the position of the
picture in that game's avatar list.

When it is read
---------------

- **Prime, Prime 2, XX, Phoenix:** at every login. Change the file and your
  next login shows the new name or avatar. The machine never writes to it,
  except for the name of the machine's own default profiles (next section).
- **NX2, NX Absolute, Fiesta, Fiesta EX, Fiesta 2:** once, when the game finds
  no save of its own on the stick and one is created. Afterwards the game's
  save rules (:ref:`online_usb_existing_section`).

The name of the machine's default profiles
------------------------------------------

For ``/SETTINGS/profiles/P1`` and ``P2`` only, the menu writes ``name=``
itself: the name of your license. It keeps doing so (for example after the
machine gets another license) for as long as the name is still the one it
wrote. Once you type a name of your own, the menu leaves it alone. Nothing
else in the file is ever written for you, and profiles on USB sticks are
never renamed.
