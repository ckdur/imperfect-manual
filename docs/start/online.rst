.. _online_section:

Profiles and Online Play
~~~~~~~~~~~~~~~~~~~~~~~~

The games that originally needed the manufacturer's servers or an AM.PASS card
keep working on the *Imperfect Collection*: every machine runs its own small
game server next to the game. Your profile (name, avatar, best scores) is kept
**on the machine or on your own USB stick**, never on a server on the
internet. The internet is used for one thing only: finding an opponent for
**Online Matching**.

Which game does what
--------------------

.. list-table::
   :header-rows: 1
   :widths: 30 35 35

   * - Game
     - Profile
     - Online Matching
   * - Phoenix, XX
     - Machine or USB stick
     - Yes
   * - Prime 2, Prime
     - Machine or USB stick
     - No (the games have no such mode)
   * - NX2, NX Absolute, Fiesta, Fiesta EX, Fiesta 2
     - USB stick (the game's own save)
     - No

Without a network cable everything still works, except Online Matching.

Where the files are
-------------------

There are two places: the **SETTINGS partition** of the machine's disk and the
**player's USB stick**.

.. list-table::
   :header-rows: 1
   :widths: 45 55

   * - File
     - What it is
   * - ``/SETTINGS/online.ini``
     - Network settings of the machine. Written with the defaults the first
       time one of Prime, Prime 2, XX or Phoenix starts.
   * - ``/SETTINGS/profiles/P1/profile.ini``, ``/SETTINGS/profiles/P2/profile.ini``
     - The machine's two **default profiles**, used by whoever plays on that
       side without a USB stick. Created by the menu as soon as the machine
       is licensed, named after your license.
   * - ``/SETTINGS/profiles/P1/save.json`` (and ``P2``)
     - Scores of that default profile. Written by the machine: do not edit.
   * - ``/SETTINGS/profiles/cards/<card number>/``
     - Same two files for every real AM.PASS card that was used on the
       machine.
   * - ``<USB stick>/ntdec/profile.ini``
     - **Your own profile.** Same format as the default profiles.
   * - ``<USB stick>/ntdec/save.json``
     - Your scores in Prime, Prime 2, XX and Phoenix.
   * - ``<USB stick>/nx2save.bin``, ``fiesta_save.bin``, ``prime.bin`` ...
     - The older games' own files, in the root of the stick. They are created
       for you (see below); leave them where they are.
   * - ``/SETTINGS/piu_server.log``
     - What the game server did during the last game: who logged in, from
       where, and whether the match service was reached.

The SETTINGS partition is the second partition of the disk (ext2). To edit a
file there, connect the disk to a computer running Linux (or boot the cabinet's
computer from a Linux USB stick) and open that partition. A USB stick is plain
FAT32 and can be edited on any computer.

The profile file (``profile.ini``)
----------------------------------

A text file. The same format is used on a USB stick and for the machine's
default profiles:

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

   [fiesta]
   avatar=6

- ``[profile]`` ``name=`` is your name in every game. Use letters ``A-Z`` and
  digits. Up to 12 characters; XX, Prime 2 and Prime show 11; NX2 and NX
  Absolute show 8.
- Every other section belongs to one game, and everything in it is optional.
  ``name=`` inside a game's section replaces the general name in that game
  only.
- ``avatar=``, ``title=`` and ``country=`` are the game's own numbers:

.. list-table::
   :header-rows: 1
   :widths: 25 25 50

   * - Section
     - Game
     - Values
   * - ``[phoenix]``
     - Phoenix
     - ``avatar`` 0-164, ``country`` 0-247 (the flag next to your name,
       0 = none)
   * - ``[xx]``
     - XX
     - ``avatar`` 69-163, ``title`` 0-199 (109 = no title)
   * - ``[prime2]``
     - Prime 2
     - ``avatar`` 0-39
   * - ``[prime]``
     - Prime
     - ``avatar`` 0-39
   * - ``[nx2]``
     - NX2
     - ``avatar`` 0-127
   * - ``[nxa]``
     - NX Absolute
     - ``avatar`` 0-163
   * - ``[fiesta]``
     - Fiesta
     - ``avatar`` 0-214
   * - ``[fex]``
     - Fiesta EX
     - ``avatar`` 0-234
   * - ``[fiesta2]``
     - Fiesta 2
     - ``avatar`` 0-259

The machine's two default profiles carry **the name of your license**. The
menu writes it there, and updates it if the machine gets another license, for
as long as you have not typed a name of your own: once you change ``name=``
in ``/SETTINGS/profiles/P1/profile.ini`` (or ``P2``), it is yours and the menu
leaves it alone. Only that one line is ever written for you; profiles on USB
sticks are never renamed.

A value you leave out gets a default (a random avatar, chosen once). The file
is read every time you log in and is never changed by the machine, so in
Prime, Prime 2, XX and Phoenix a new name or avatar shows up at your next
login.

Using a USB stick
-----------------

1. Format a stick as **FAT32** (one partition, as sticks come from the shop).
2. Create a folder named ``ntdec`` on it and put your ``profile.ini`` inside.
   If you skip this step, the folder and a ready-to-edit ``profile.ini`` are
   created the first time you log in with the stick on Prime, Prime 2, XX or
   Phoenix.
3. Plug the stick into **your side's USB port** before you log in.

What happens then depends on the game:

- **Prime 2, XX, Phoenix.** Log in the usual way (see *Logging in* below). With
  your stick in your port, the profile on the stick is used instead of the
  machine's default one, and your scores are written to the stick after every
  song. The stick is only in use for an instant each time: you can pull it
  out between songs.
- **Prime.** The game logs you in from the stick by itself once a credit is
  in. The stick gets a small file, ``prime.bin``: it is your identity in this
  game, keep it.
- **NX2, NX Absolute, Fiesta, Fiesta EX, Fiesta 2.** These games keep their
  own save on the stick. If the stick has none, one is created with the name
  and avatar of your ``profile.ini``, and the game loads it at once. You no
  longer need to bind the USB ports in each game's service menu.

.. note::

   A save that is already on the stick is **never replaced** and
   ``profile.ini`` is not looked at: a profile you have been playing with,
   here or on another machine, loads exactly as before. The same holds when
   the stick has the save of the previous game, which the newer game carries
   over by itself (NX2 to NX Absolute; Fiesta to Fiesta EX to Fiesta 2).
   These older games cannot change a name or an avatar afterwards: to start
   over, delete the game's two ``.bin`` files from the stick.

What the older games need of a stick: FAT32, a normal partition (not a stick
formatted without one), and plugged directly into the machine (not through a
hub). In Fiesta and Fiesta EX a name beginning with ``PIU`` counts as "not
registered": choose another one.

Which USB port is whose
-----------------------

Out of the box, when one stick is plugged in it belongs to player 1, and a
second one to player 2 (the lower port number is player 1). That is wrong as
soon as player 2 comes alone, so tell the machine once which port is which:

1. Plug a stick into the port you want for player 1, start one of Prime,
   Prime 2, XX or Phoenix, then look at ``/SETTINGS/piu_server.log``. A line
   like this names the port::

      usb: stick on port 4-1 (/dev/sdb)

2. Do the same for player 2's port.
3. Write both into ``/SETTINGS/online.ini``:

.. code-block:: ini

   [usb]
   p1=4-1
   p2=4-2

The setting applies to every game above, the older ones included. Several
ports can be given for a side, separated by spaces.

Logging in (Prime 2, XX, Phoenix)
---------------------------------

These games log a player in when a card touches the reader of that side.

- **With real AM.PASS readers** nothing changes: touch your card. A card the
  machine has never seen gets its own profile on the machine; with your USB
  stick in your port, the stick's profile is used instead.
- **Without readers**, the machine behaves as if a card were resting on each
  reader: insert a credit and both sides are logged in by themselves a few
  seconds later, each with its default profile, or with the profile of the
  stick in its port. Press the centre step on the side you want to play on.

**Prime** has no card: once a credit is in, each side is logged in by itself,
from the stick in its port or else with the machine's default profile.

The card readers are assigned to the players automatically. If you ever need
to do it by hand (SETUP MENU, CARD READER): touch a card first, *then* select
the player.

The emulated cards are configured per game in ``ampass.ini``, inside the
game's own folder on SETTINGS: ``/SETTINGS/F17`` (Prime 2), ``/SETTINGS/F19``
(XX), ``/SETTINGS/F23`` (Phoenix). The one setting worth knowing is
``repeat_ms``: ``3000`` leaves the card on the reader as described above;
``0`` takes it away, for a machine that should only log in real cards. On a
machine updated from an older version the file already exists with
``repeat_ms=0``: change it to ``3000`` to get the behaviour described here.

Online Matching (XX and Phoenix)
--------------------------------

1. Connect the machine to the internet with a network cable (the address is
   taken automatically, by DHCP). The game itself is still kept off the
   internet: only the match service is reachable.
2. Log in and reach song select **alone** (one player on the machine).
3. Press the **upper-left** arrow to open the channel list, move with the
   lower arrows to **ONLINE MATCHING** and press the centre step.
4. Pick a level range and press the centre step three times.

The game then looks for another machine doing the same in the same game.
When it finds one, both screens show the two players, and the song, the
result and the comparison follow by themselves.

The **ONLINE MATCHING** channel is only in the list while there is somebody
to play against, that is while the machine reaches the match service. If it
is missing, check the cable and ``/SETTINGS/piu_server.log``: it says
``match service online`` or why the service was not reached.

The network file (``online.ini``)
---------------------------------

.. code-block:: ini

   [online]
   enabled=1
   server=wss://piu.ckdur.dev/
   token=
   tls_verify=1
   lan_server=

   [usb]
   enabled=1
   p1=
   p2=

- ``enabled`` – ``0`` never uses the network. Profiles work the same.
- ``server`` – the match service. Leave the default unless you run your own.
- ``token`` – access token of the service. Leave it empty: the system carries
  the one for the default service.
- ``tls_verify`` – set to ``0`` only if the log says the service's
  certificate "is not yet valid": the machine's clock is wrong (usually a
  dead battery on the mainboard). Setting the clock is the better fix.
- ``lan_server`` – address of **another** *Imperfect Collection* machine on
  your network. The games of this machine then use that machine's game
  server: its profiles, and matching between the machines connected to it,
  with or without internet. Leave it empty on the machine that the others
  point to.
- ``[usb]`` ``enabled`` – ``0`` ignores USB sticks for profiles.
- ``[usb]`` ``p1``, ``p2`` – which USB port belongs to which player, see
  above.

Changes are picked up the next time a game starts.
