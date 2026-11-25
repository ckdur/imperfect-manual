.. _online_settings_page_section:

Settings page
~~~~~~~~~~~~~

**Where:** ``http://<cabinet>:8080/settings/`` (the **Settings** link in the
header of every page; the address of the cabinet is the one of the F8 QR code).
It also opens when the machine has no valid license, so a licensing problem
never locks the operator out.

Anyone on the network can **read** the settings. **Changing** them needs the
**operator key**: at the cabinet, open the menu's settings and choose
**System Information**; the key is the "Operator Key" line. Each machine makes
its own random key the first time it starts. It is the **only** operator key:
the same one opens this page, the pads page, the **USB ports** page, the **PMod
songs** page and the license page when it replaces a valid license. The old
``[web] operator_key=`` line is deprecated: a machine that had it keeps that
value as its key (it is copied to ``press_key``), and if both were set,
``press_key`` wins. Each of these pages asks for the key and keeps it only in
the open tab; closing the tab forgets it. The USB ports page still lists the
sticks without a key, but changing a port needs it.

Settings are in two groups:

* **Normal**: the match service address, the LAN server, the QR code, the
  names in the side bars, the live pages (live scores, now playing, the pads),
  the song cache and the PMod limits.
* **Dangerous**: the certificate check of the match service, USB sticks and
  their ports, the web's own switch and port, and **pressing the pads from the
  web**. They are shown in their own block under a warning, and saving one asks
  you to tick "I understand". A wrong value can lock you out of the page or
  send saves to the wrong player.

Each setting says when it applies: **at once**, **at the next game start** or
**after the next restart**. The last 10 changes are listed at the bottom of the
page (the file is ``/SETTINGS/settings_changes.log``: time, address of the
device, setting, old and new value; keys are never written to it). Until you
unlock the page with the key, the list shows the time, the setting and the old
and new value, but not the address of the device that made the change.

.. _insert-profile:

Profiles in the running game
----------------------------

While a game runs, the section *Profiles in the running game* puts any profile
of the machine into it as player 1 or player 2: the two machine default
profiles and every AM.PASS card profile (``/SETTINGS/profiles/cards/<uid>``).
It is a control of the machine, like pressing its pads, so it is shown only
after you unlock the page with the operator key; every **Insert as P1**,
**Insert as P2** and **Remove** asks you to confirm first and is written to the
change log. On the home page, a player card shows **Put into the game** when the
running game can take that profile; it opens this section.

- **NX2, NXA, Fiesta, Fiesta EX, Fiesta 2**: cards and both machine profiles,
  on either side. The profile becomes that side's USB stick (put it in on the
  "insert USB memory" screen); **Remove** pulls it out.
- **Prime 2, XX, Phoenix**: cards and both machine profiles, on either side.
  The profile is the card lying on that side's reader; **Remove** takes the
  card off the reader, so that side no longer logs in by itself.
- **Prime, Prime JE**: cards.
- **Infinity**: cards; **Remove** pulls the card's stick.
- **1st .. NX**: cards and the side's own machine profile (the profile the
  plays are recorded in).
- **The menu, PMod and anything else**: nothing; the page says so.

A USB stick in a side's port always wins: the page refuses to put a card or a
machine profile on that side until it is pulled out. In Prime 2, XX and
Phoenix the stick itself can be put in for its own side. Profiles on sticks
are not inserted on another side: the game reads a stick only on the port
bound to a player (:ref:`online_web_ini_section`, ``[usb] p1=`` / ``p2=``).

Changing the operator key
-------------------------

On the same page, under *Change the operator key*: 8 to 64 characters, no
spaces, no ``;`` and no ``#``. The new key works at once, also for the pads
page, the autoplay switch, the USB ports page, the PMod songs page and the
license page.

If you lose the key
-------------------

Read it again in System Information. Without the menu, delete the
``press_key=`` line of ``/SETTINGS/online.ini`` (from a USB stick or on the
machine itself): a new random key is made the next time the machine starts.

Wrong keys
----------

After a wrong key the device has to wait a moment; after five wrong keys in a
row it is locked out for a minute, and longer each time (up to 15 minutes).
The same protection covers the pads page, the autoplay switch, the USB ports
page, the PMod songs page and the license page: wrong keys on one of them
count for all.

What is not protected
---------------------

The cabinet's web is plain HTTP on your own network. Someone who can listen to
that network can see the key when it is sent, and anyone who can open
System Information at the cabinet can read it. Keep the cabinet on a network
you trust.
