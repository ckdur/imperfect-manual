.. _online_login_section:

Logging In
~~~~~~~~~~

Prime 2, XX and Phoenix
-----------------------

These games log a player in when a card touches the reader of that side.

**With real AM.PASS readers**
  Nothing changes: touch your card. A card the machine has never seen gets
  its own profile on the machine. With your USB stick in your port, the
  stick's profile is used instead.

**Without readers**
  The machine behaves as if a card were resting on each reader: insert a
  credit and both sides are logged in by themselves a few seconds later, each
  with the machine's default profile for that side, or with the profile of
  the stick in its port. Then press the centre step on the side you want to
  play on.

The card readers are assigned to the players automatically. If you ever need
to do it by hand (*SETUP MENU*, *CARD READER*): touch a card first, **then**
select the player. Selecting first clears the assignment.

.. note::

   On a machine that was updated from an older version, the card emulation
   file already exists and still says "do not leave the card on the reader".
   If nobody is logged in after a credit, change ``repeat_ms`` as described in
   :ref:`online_ampass_ini_section`.

Prime and Prime JE
------------------

Prime and Prime Japanese Edition have no card. Once a credit is in, each side is logged in by itself:
from the stick in its port, or else with the machine's default profile. With
an AM.PASS card reader attached you can tap a card instead
(:ref:`online_card_profiles_section`); the default profile then waits 8
seconds for a tap before it logs in.

NX2, NX Absolute, Fiesta, Fiesta EX, Fiesta 2
---------------------------------------------

There is no login: the game loads the profile of the stick in your port when
you join. With no stick, tap an AM.PASS card on your side's reader and the
card's profile is used instead (:ref:`online_card_profiles_section`).
Without either you play without a profile, as on the original machine.

Changing the default profiles
-----------------------------

The two default profiles are the files
``/SETTINGS/profiles/P1/profile.ini`` and ``/SETTINGS/profiles/P2/profile.ini``
(:ref:`format <online_profile_ini_section>`). They are shipped with the image,
and the menu **names them after your license** as soon as the machine is
licensed (and creates them if they are missing). The menu keeps
that name in step with the license until you type one of your own: from then
on it is yours and is left alone.
