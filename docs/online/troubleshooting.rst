.. _online_trouble_section:

When Something Does Not Work
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Start with ``/SETTINGS/piu_server.log`` (:ref:`how to reach it
<online_files_settings_section>`). It is rewritten every time Prime,
Prime 2, XX or Phoenix starts, and holds what happened during that game.

Lines you will see
------------------

.. list-table::
   :header-rows: 1
   :widths: 46 54

   * - Line
     - Meaning
   * - ``match service online: wss://...``
     - The machine reached the match service. Online Matching is available.
   * - ``match service not reachable: ...``
     - No Online Matching for now; everything else works. The reason follows:
       a name that does not resolve or "Network is unreachable" is a cable or
       network problem.
   * - ``... certificate ... (check the machine's clock, or set tls_verify=0)``
     - The machine's clock is wrong, so the service's certificate looks
       invalid. See ``tls_verify`` in :ref:`online_online_ini_section`.
   * - ``match service not reachable: refused: bad token``
     - The service did not accept this system's token. Leave ``token=`` empty
       unless you were given one.
   * - ``match service off (no [online] server)``
     - ``enabled=0`` or an empty ``server=`` in ``online.ini``: the machine
       does not look for the match service.
   * - ``default route via ... removed (the game stays off the network)``
     - Normal: the game is cut off from the internet, only the match service
       stays reachable.
   * - ``usb: stick on port 4-1 (/dev/sdb)``
     - A stick that was plugged in when the game started, and the name of
       its port (:ref:`online_usb_ports_section`).
   * - ``profile usb P1 (port 4-1): #... NAME``
     - Player 1 logged in with the profile of the stick in that port.
   * - ``profile default P1: #... NAME``
     - Player 1 logged in with the machine's default profile.
   * - ``profile card ...: #... NAME``
     - A real card logged in with its own profile on the machine.
   * - ``usb: stick on port ... has no usable filesystem ... it must be FAT32``
     - The stick is not FAT32, or has no partition the system can read. The
       machine's default profile was used instead.
   * - ``...: stick not there, records kept in memory until it is back``
     - The stick was pulled out before a score could be written. Plug the
       same stick back in: the score is written together with the next one,
       as long as the game has not been closed in between.
   * - ``...: another profile's stick is in the port, not saving``
     - A different player's stick is now in that port: nothing is written to
       it.

Common situations
-----------------

**Nobody is logged in after inserting a credit (Prime 2, XX, Phoenix).**
  On a machine updated from an older version, see the note in
  :ref:`online_ampass_ini_section`.

**The game says OFFLINE.**
  The game could not reach the server that runs next to it. Check that the
  log exists and was written just now; if it was not, the server did not
  start.

**My stick is used for the wrong player.**
  Assign the ports: :ref:`online_usb_ports_section`.

**An older game says the USB drive is not working, or does not see it.**
  The stick must be FAT32 with a normal partition, and plugged directly into
  the machine. Some very small or unusual sticks report no serial number and
  are ignored by these games: try another stick.

**I changed the name in profile.ini but an older game still shows the old
one.** NX2 to Fiesta 2 only read ``profile.ini`` when they create their
save. Delete that game's two ``.bin`` files from the stick to start over
(:ref:`online_usb_existing_section`).

**The ONLINE MATCHING channel is not in the list.**
  See :ref:`online_matching_section`.

**The importer refuses to import after the disk was written again.**
  That is about the license, not about this chapter:
  :ref:`license_import_section`.
