.. _online_overview_section:

What Each Game Does
~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 26 26 24 24

   * - Game
     - Where the profile lives
     - How you log in
     - Online Matching
   * - Phoenix, XX
     - Machine, or your USB stick
     - Card on the reader (real or emulated)
     - Yes
   * - Prime 2
     - Machine, or your USB stick
     - Card on the reader (real or emulated)
     - No (the game has no such mode)
   * - Prime, Prime JE
     - Machine, or your USB stick
     - By itself, once a credit is in
     - No (the game has no such mode)
   * - NX2, NX Absolute, Fiesta, Fiesta EX, Fiesta 2
     - Your USB stick (the game's own save)
     - The game reads the stick
     - No

Prime Japanese Edition (V1.17.0) plays online exactly like Prime: it talks to
the game server that runs next to it on the machine (it connects to port
60006, where Prime uses another one), so it logs in and keeps profiles the
same way.

A few things hold for all of them:

- **Nothing leaves the machine except the search for an opponent.** Names and
  scores are stored in files you can see and copy
  (:ref:`where they are <online_files_section>`).
- **No network, no problem.** Without a cable everything works except Online
  Matching.
- **One profile file for every game.** The same ``profile.ini`` holds your
  name and the avatar you want in each game
  (:ref:`its format <online_profile_ini_section>`), whether it sits on a USB
  stick or is one of the machine's two default profiles.
- **Profiles can be managed from a phone.** Press F8 on a keyboard and scan
  the code: :ref:`online_web_section`.
- **The machine's default profiles** are for whoever plays without a stick:
  one for the left side (P1) and one for the right side (P2). They are named
  after your license until you give them a name of your own.

Which versions are used
-----------------------

Two of the games run an earlier build than the last one released, because
the later build has no network code left in it and could not log anybody in:

- **XX** runs 2.08.2 (not 2.08.3).
- **Prime 2** runs 2.05.0 (not 2.05.1).
