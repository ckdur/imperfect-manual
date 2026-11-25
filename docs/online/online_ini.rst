.. _online_online_ini_section:

Reference: online.ini
~~~~~~~~~~~~~~~~~~~~~

**Where:** ``/SETTINGS/online.ini`` (:ref:`online_files_section`). It is **shipped with the image** and written again
with the same defaults if it is missing (for example on a machine updated
from an older version, the first time Prime, Prime 2, XX or Phoenix starts);
yours from then on. Changes are picked up the next time a game starts.

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

   [web]
   enabled=1
   port=8080
   qr_key=F8
   qr_seconds=10
   qr_side=right
   qr_size=0.33
   url=
   side_names=1

The ``[online]`` section
------------------------

.. list-table::
   :header-rows: 1
   :widths: 18 14 68

   * - Key
     - Default
     - Meaning
   * - ``enabled``
     - ``1``
     - ``0`` never uses the network. Profiles work the same; there is no
       Online Matching.
   * - ``server``
     - ``wss://piu.ckdur.dev/``
     - The match service. Leave the default unless you run your own.
   * - ``token``
     - empty
     - Access token of the service. Leave it empty: the system carries the
       one for the default service.
   * - ``tls_verify``
     - ``1``
     - ``0`` skips the check of the service's certificate. Only for a
       machine whose clock is wrong (the log then says the certificate "is
       not yet valid"); setting the clock is the better fix.
   * - ``lan_server``
     - empty
     - Address of **another** machine on your network. The games of this
       machine then use that machine's game server instead of their own,
       see :ref:`online_matching_section`. Leave it empty on the host.

The ``[usb]`` section
---------------------

.. list-table::
   :header-rows: 1
   :widths: 18 14 68

   * - Key
     - Default
     - Meaning
   * - ``enabled``
     - ``1``
     - ``0`` ignores USB sticks for profiles.
   * - ``p1``
     - empty
     - The USB port of player 1, as named in the server log (for example
       ``4-1``). Several ports can be listed, separated by spaces; ``*`` and
       ``?`` are allowed.
   * - ``p2``
     - empty
     - The USB port of player 2.

With ``p1`` and ``p2`` both empty, the stick on the lowest port is player 1
and the next one player 2. The profile web's **USB ports** page sets both
by plugging a stick in, and how to find the port names by hand:
:ref:`online_usb_ports_section`. A change takes effect without a restart.

.. _online_web_ini_section:

The ``[web]`` section
---------------------

Settings of the :ref:`Profile manager <online_web_section>`.

.. list-table::
   :header-rows: 1
   :widths: 18 14 68

   * - Key
     - Default
     - Meaning
   * - ``enabled``
     - ``1``
     - ``0`` does not start the page.
   * - ``port``
     - ``8080``
     - The port of the page.
   * - ``qr_key``
     - ``F8``
     - The keyboard key that shows the QR code: a key name (``F8``,
       ``HOME``, ``KP5``, ``A`` .. ``Z``, ``0`` .. ``9``). The game sees the
       key too: the keyboard emulation of the games also maps F5 to F12 to
       test and service buttons, so pick another key if that matters.
   * - ``qr_seconds``
     - ``10``
     - How long the code stays on the screen. Pressing the key again
       restarts the time.
   * - ``qr_side``
     - ``right``
     - ``left`` or ``right``: the side bar of the picture in which the code
       is drawn. While the players' names are in the side bars (games up to
       NX) the code is always at the bottom of the right bar
       (:ref:`online_side_names_section`).
   * - ``qr_size``
     - ``0.33``
     - Height of the code as a fraction of the screen height (``0.1`` to
       ``0.8``). On a 4:3 picture the code may cover the edge of the game
       while it is shown.
   * - ``url``
     - empty
     - The address the code stands for. Empty: ``http://<address of the
       cabinet>:<port>/``. Set it only if phones reach the cabinet under
       another name or address.
   * - ``side_names``
     - ``1``
     - ``0`` turns off the players' profile names in the side bars of the
       games up to NX (:ref:`online_side_names_section`).
   * - ``operator_key``
     - empty
     - **Deprecated.** There is now one operator key for everything,
       ``[stream] press_key`` (the :ref:`settings page <online_settings_page_section>`,
       the :ref:`USB ports page <online_usb_ports_section>`, the
       :ref:`PMod songs page <online_web_pmod_section>`, the license page and
       the pads page). If you had set this line, the machine takes its value
       as the single key the first time it starts, unless ``press_key`` was
       already chosen by hand (then ``press_key`` wins and this line is
       ignored). It is kept for one more release and never written again;
       delete it once the key works.
   * - ``pmod_upload_mb``
     - ``1024``
     - Largest upload (MB) of the :ref:`PMod songs page <online_web_pmod_section>`.
   * - ``pmod_max_files``
     - ``20000``
     - Most files one uploaded zip may hold.
   * - ``pmod_unpacked_mb``
     - ``4096``
     - Most MB one uploaded zip may unpack to.

.. warning::

   The page has **no login and is open to anyone on the same network as the
   cabinet**, and it is on whenever the machine is on, in the menu and in
   every game. Whoever opens it can change the profiles of the players. Keep
   the cabinet on a network you trust and never expose it to the internet, or
   set ``enabled=0``.

The page shows nothing without a valid license, and the page of a game only
when that game is installed.

.. _online_stream_ini_section:

The ``[stream]`` section
------------------------

Settings of the :ref:`live pages for streamers <online_streaming_section>`.
They are read at every request: no restart is needed.

.. list-table::
   :header-rows: 1
   :widths: 18 14 68

   * - Key
     - Default
     - Meaning
   * - ``enabled``
     - ``1``
     - ``0`` turns the live pages off (they are on by default). Off, they answer "live pages are off on
       this machine" and the Profile manager is not affected.
   * - ``names``
     - ``1``
     - ``0`` hides the names of the players: this machine's and the online
       opponent's.
   * - ``pads``
     - ``1``
     - ``0`` hides the pad presses and the lights.
   * - ``press``
     - ``0``
     - ``1`` lets the operator **press** the pads and the service, test and
       coin buttons from the pads page (see
       :ref:`online_streaming_section`). It also needs ``press_key``.
   * - ``press_key``
     - empty
     - The operator key the pads page asks for before it may press. Empty:
       nobody may press, whatever ``press`` says.
