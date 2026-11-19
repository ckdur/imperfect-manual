.. _online_usb_section:

USB Sticks
~~~~~~~~~~

Preparing a stick
-----------------

1. Format a stick as **FAT32**, with one partition, the way sticks come from
   the shop.
2. Create a folder named ``ntdec`` on it and put a file ``profile.ini`` inside
   (:ref:`format <online_profile_ini_section>`). The shortest useful one is:

   .. code-block:: ini

      [profile]
      name=CKDUR

   If you skip this step, the folder and a ready-to-edit ``profile.ini`` are
   created the first time you log in with the stick on Prime, Prime 2, XX or
   Phoenix.
3. Plug the stick into **your side's USB port** before you log in.

What the older games need of a stick, besides FAT32: a normal partition (not
a stick formatted without a partition table), and to be plugged directly into
the machine, not through a hub.

What happens in each game
-------------------------

**Prime 2, XX, Phoenix**
  Log in the usual way (:ref:`online_login_section`). With your stick in your
  port, the profile on the stick is used instead of the machine's default
  one, and your scores are written to the stick after every song. The stick
  is only in use for an instant each time: you can pull it out between songs.

**Prime, Prime JE**
  The game logs you in from the stick by itself once a credit is in, in both
  versions. The stick gets a small file, ``prime.bin``: it is your identity
  in this game, keep it.

**NX2, NX Absolute, Fiesta, Fiesta EX, Fiesta 2**
  These games keep their own save on the stick. If the stick has none, one is
  created with the name and avatar of your ``profile.ini`` and the game loads
  it at once. You do not have to bind the USB ports in each game's service
  menu any more.

  On a stick with no ``profile.ini`` (or with no ``name=`` in it), NX2 and
  NX Absolute get a profile with a random name of the form ``PIU1234``, and
  Fiesta, Fiesta EX and Fiesta 2 create their own profile as they always
  did. Write ``profile.ini`` first if you want your name.

.. _online_card_profiles_section:

AM.PASS cards instead of a stick
--------------------------------

On NX2, NX Absolute, Fiesta, Fiesta EX, Fiesta 2 (the Chinese builds of NX2
and NX Absolute too), Prime and Prime JE you can also play with an AM.PASS
card, and it needs no stick. Tap the card on a card reader: **reader 1 is
player 1 and reader 2 is player 2**. That side then has a profile of its own
for that card, which works exactly as a stick would.

- **Where it lives.** The folder ``/SETTINGS/profiles/cards/<card number>/``
  acts as that player's USB stick: the game's save files are in it under the
  same names as on a stick, and ``profile.ini`` sits at its top
  (:ref:`where the files are <online_files_section>`). It is the same folder
  that Prime 2, XX and Phoenix use for that card, so one card has one folder
  for every game. Copying the folder onto a FAT32 stick makes it that stick.
- **A real stick always wins.** A stick in the player's port is used and the
  card is ignored for that side.
- **First use.** The profile is named ``CARD`` plus the last four hex digits
  of the card number (for example ``CARDE5F6``): a name every game accepts.
  If the card already has a ``profile.ini`` (it played XX first, or you
  changed the name on the :ref:`Profile manager <online_web_section>`), that
  name is used.
- **Each card is its own profile.** Cards never share a save, and a card that
  is in use on one side is refused on the other.
- **How long it lasts.** From the tap until the game lets go of the profile:
  in NX2 and NX Absolute that is when the title screen comes back, so the
  next player taps a card of their own. Tapping another card on the same
  side swaps to it. A card left lying on the reader counts as one tap.
- **Prime and Prime JE** log the card in by its number, into the same folder
  as Prime 2, XX and Phoenix. With a card reader plugged in, the default
  login (no stick, no card) waits 8 seconds for a tap instead of a few
  moments, so you have time to tap.

Known limit: on the Fiesta games a card may stay with its side after the
song session, until another card is tapped there or the game exits.

``[usb] enabled=0`` in ``online.ini`` turns cards off together with sticks.

.. _online_usb_existing_section:

Sticks that already have a profile
----------------------------------

A save that is already on the stick is **never replaced**, and
``profile.ini`` is not even looked at: a profile you have been playing with,
here or on another machine, loads exactly as before.

The same holds when the stick has the save of the previous game, which the
newer game carries over by itself:

- NX2 to NX Absolute;
- Fiesta to Fiesta EX to Fiesta 2.

These older games cannot change a name or an avatar afterwards. To start
over, delete the game's two ``.bin`` files from the stick
(:ref:`their names <online_files_stick_section>`).

In Fiesta and Fiesta EX a name beginning with ``PIU`` counts as "not
registered", and Fiesta 2 does not carry over a Fiesta EX save with such a
name: choose another one.

.. _online_usb_ports_section:

Which USB port is whose
-----------------------

Out of the box, a single stick belongs to player 1 and a second one to
player 2 (the lower port number is player 1). That is wrong as soon as
player 2 comes alone, so tell the machine once which port is which.

**The easy way: the profile web's USB ports page.** Open the cabinet's
profile web (:ref:`how <online_web_section>`) and choose
**USB ports** at the top. It lists the sticks plugged in now, with their
port and the player each one counts as, and refreshes by itself.

* Plug a stick into the port meant for player 1 and press **Assign to P1**
  on its line; the same for player 2. Or press **Assign P1: plug the stick
  now** and plug a stick within 30 seconds: whatever port it lands in
  becomes player 1's, so you never have to tell the ports apart.
* **Clear** forgets one side, **Swap P1 and P2** exchanges them. A port
  given to one player is taken away from the other.
* A stick behind a USB hub is shown with a warning: NX2, NXA, Fiesta and
  Fiesta EX only see sticks in a port of the machine itself (Fiesta 2 and
  Prime also behind a hub in its first port); Prime 2, XX and Phoenix see
  any port.
* The page writes ``[usb] p1=`` / ``p2=`` into ``/SETTINGS/online.ini`` and
  leaves the rest of the file as it was. It takes effect at once: the next
  login reads it, and a game that is running (NX2 to Fiesta 2, Prime)
  follows it within a second. No restart is needed.
* To keep visitors of the page from changing it, set an operator key in
  ``/SETTINGS/online.ini``: ``[web]`` ``operator_key=<something>``. The page
  then asks for it before every change.

**By hand**, as before:

1. Plug a stick into the port you want for player 1, start one of Prime,
   Prime 2, XX or Phoenix, then read ``/SETTINGS/piu_server.log``
   (:ref:`how to reach it <online_files_settings_section>`). A line like
   this names the port::

      usb: stick on port 4-1 (/dev/sdb)

2. Do the same for player 2's port.
3. Write both into ``/SETTINGS/online.ini``
   (:ref:`format <online_online_ini_section>`):

   .. code-block:: ini

      [usb]
      p1=4-1
      p2=4-2

The setting applies to every game of this chapter, the older ones included.
