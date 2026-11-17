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

**Prime**
  The game logs you in from the stick by itself once a credit is in. The
  stick gets a small file, ``prime.bin``: it is your identity in this game,
  keep it.

**NX2, NX Absolute, Fiesta, Fiesta EX, Fiesta 2**
  These games keep their own save on the stick. If the stick has none, one is
  created with the name and avatar of your ``profile.ini`` and the game loads
  it at once. You do not have to bind the USB ports in each game's service
  menu any more.

  On a stick with no ``profile.ini`` (or with no ``name=`` in it), NX2 and
  NX Absolute get a profile with a random name of the form ``PIU1234``, and
  Fiesta, Fiesta EX and Fiesta 2 create their own profile as they always
  did. Write ``profile.ini`` first if you want your name.

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
player 2 comes alone, so tell the machine once which port is which:

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
