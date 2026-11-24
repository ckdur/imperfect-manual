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
its own random key the first time it starts.

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
device, setting, old and new value; keys are never written to it).

Changing the operator key
-------------------------

On the same page, under *Change the operator key*: 8 to 64 characters, no
spaces, no ``;`` and no ``#``. The new key works at once, also for the pads
page and the autoplay switch.

If you lose the key
-------------------

Read it again in System Information. Without the menu, delete the
``press_key=`` line of ``/SETTINGS/online.ini`` (from a USB stick or on the
machine itself): a new random key is made the next time the machine starts.

Wrong keys
----------

After a wrong key the device has to wait a moment; after five wrong keys in a
row it is locked out for a minute, and longer each time (up to 15 minutes).
The same protection covers the pads page and the autoplay switch.

What is not protected
---------------------

The cabinet's web is plain HTTP on your own network. Someone who can listen to
that network can see the key when it is sent, and anyone who can open
System Information at the cabinet can read it. Keep the cabinet on a network
you trust.
