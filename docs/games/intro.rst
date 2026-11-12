Information about the games
---------------------------

.. _games_compat_section:

This section lists information per game release. Some things apply to all of
them:

- **Compatibility.** Under the virtual machine test harness (see
  :doc:`../dev/building`), all 32 supported game entries boot and run with
  the current graphics stack (Mesa 23.3 over DRI3).
- **Phoenix.** Phoenix 2.12 boots with the loader, and the importer recognizes
  2.13.
- **Prime, Prime 2 and XX.** These start and stay up. They use the AM.PASS
  reader emulator (``ampass.so``, covering Prime 2 up to Phoenix), and a local
  game server (``piu_server.py``) is started for the titles that expect an
  online connection (XX, Prime 2 and Prime), with a network redirect library
  for Prime.
- **Sound and video.** The games use ffmpeg 4.4.4; PMOD uses ffmpeg 8.0.

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   100
   200
   300
   400
   450
   500
   550
   600
   650
   700
   750
   800
   850
   A00
   B00
   C00
   D00
   E00
   F00
   F10
   F11
   F12
   F13
   F15
   F17
   F19
   F23
