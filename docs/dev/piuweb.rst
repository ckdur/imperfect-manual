.. _piuweb_dev_section:

The profile manager (piuweb)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How the :ref:`Profile manager <online_web_section>` is built. The source of
truth is the repository: ``elfloader/server/piuweb/DESIGN.md`` (the contract
between the parts) and ``README.md``; the save layouts are in
``cpio_trap/menugl/usbprofile/FORMATS.md`` ("NX2/NXA body", "Fiesta family
body", "Machine unlocks") and the song data in
``elfloader/server/piuweb/songs/FORMATS.md``.

The daemon
^^^^^^^^^^

``elfloader/server/piu_web.py`` is a Python 3 standard-library HTTP daemon
serving a plain HTML/CSS/JS site and a JSON API. The menu starts it at every
menu start (``piuweb_start`` in ``cpio_trap/menugl/main.c``), but only from a
disk whose system manifest checked out (see :ref:`security_section`). It
detaches, keeps a lock so there is a single instance, and serves from boot
to power-off: it is not part of any game's process group, so game launches
do not stop it.

Gating
^^^^^^

The license check needs the pinned keys and the machine fingerprint, which
only the menu has. So the menu hands over its verdict in a file on the
tmpfs, and the daemon refuses every API call (HTTP 403) without it. A game's
page is refused when that game is not installed, using the same rule as the
menu. The menu also writes which game is running (``run_utils.c``), which
the daemon needs for the queue.

REST API (summary)
^^^^^^^^^^^^^^^^^^

All JSON; errors carry a ``code`` (``no_license``, ``not_installed``,
``no_player``, ``no_save``, ``op_refused``).

- ``GET /api/status``: machine, running game, games, players.
- ``GET /api/player/<pid>`` and ``/<game>``: summary, unlocks, records,
  missions, pending changes. ``pid`` is ``p1``, ``p2``, a stick or a card.
- ``POST /api/player/<pid>/<game>/ops``: ``buy``, ``claim``, ``set_name``,
  ``set_avatar``, ``set_title``; refused ones are reported one by one.
- ``DELETE /api/player/<pid>/<game>/pending``: clear the queue.
- ``GET /api/songs/<game>`` and ``/img/<game>/...``: titles and pictures.

Codecs and the queue
^^^^^^^^^^^^^^^^^^^^

Each older game has a codec in ``elfloader/server/piuweb/saves/`` (``nx2``,
``nxa``, ``fiesta``, ``fex``, ``fiesta2``) that loads the save files of the
stick, applies a change and writes them back with the checksums and
encryption the game expects. A load followed by a write with no change is
byte-identical; this is tested. Prices and item lists are ids and numbers only.

A change is validated against the save with the pending changes already
applied, then stored in ``ntdec/pending/<game>.json`` on the stick. It is
applied when no game using that save runs, when the game exits, or just
before the game loads: the ``savegen`` hook (``cpio_trap/menugl/savegen.c``)
asks the daemon on a local unix socket and waits a few seconds at most, then
goes on whatever the answer. The changes are checked again at that moment.
The previous files go to ``ntdec/backup/``. Newer games change ``profile.ini``
only; the daemon never writes their ``save.json``.

Songs
^^^^^

Titles, banners and avatars are read from the games' data at run time and
never shipped. On the cabinet the packages are encrypted, so the menu stages
the few files needed while no game runs, and the daemon builds a per-game
cache in ``/SETTINGS/piuweb`` that is encrypted and bound to the machine.
Deleting it only makes it rebuild.

The QR overlay
^^^^^^^^^^^^^^

``cpio_trap/menugl/qroverlay/`` is a small 32-bit C program started by the
menu once per boot. It watches the keyboards for ``qr_key`` without
grabbing them, reads the address the daemon publishes, and draws the QR
code in an X window above the running game for ``qr_seconds``. See its
README for the display rules.
