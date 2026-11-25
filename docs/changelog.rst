.. _changelog_section:

Release notes 2.0.0
===================

What changed for the people who use the machine, grouped by area. For the
history of earlier versions and the update files see :ref:`updates_section`;
for the base system (new OS, signed boot, drivers) see the *1.3.1 - 2.0.0*
entry there.

Menu
----

- **Check File Systems** in the Settings menu: checks the disk at the next
  start (settings, boot, then game partition), repairs what it can, shows the
  progress and writes the result to *System Information* (:ref:`menu
  <settings_section>`).
- **Region memory**: games with several regions open on the one you launched
  last.
- **MK3 / MK5 versions** of Prex 3 and Premiere 3 in the region selector (see
  below).
- **Credits shared** between the menu and the games, kept safe against power
  cuts, with **free play and attract** in the old games
  (:ref:`credits_section`). Prex 3 and the late MK3 games accept up to 99
  credits.
- **Translations**: the menu is complete in Spanish, Portuguese, Korean,
  Chinese and Japanese, including the language list and the System Information
  labels. The Latin accented letters of the menu font were redrawn.
- **System Information** shows the address, subnet mask, gateway and the two
  DNS servers, the disk check result and the operator key. The **IP footer is
  always drawn** (it says *not connected* with no address).
- **About** screen with the Imperfect Collection logo.
- The menu records in its log when a game is killed by a signal.
- Cabinet buttons: **TEST** moves, **SERVICE** enters and **CLEAR** goes back
  in the Settings menu; holding TEST no longer breaks the menu (see
  :ref:`menu changes <settings_section>`).

Games
-----

- **MK5 Prex 3 and MK5 Premiere 3** (source ports, SDL2) next to the original
  MK3 executables, with their own saves, the shared credits, autoplay and the
  live pages.
- **DEMO SOUND is ON by default** in the old MK3 games for new or reset
  settings, so the attract loop plays music. A machine with saved settings
  keeps its value.
- **Zero**: the game no longer shrinks to a small square in a corner while it
  loads (for example when a mission is selected).
- **Autoplay** (from the live pages): now also **1st** and **2nd**, and
  **Phoenix 2.12**.
- **Infinity**: the TEST and SERVICE buttons are swapped as in the original
  cabinet (Infinity only).
- **NX2, NX2 Chinese and NX Absolute**: the key files shipped with the
  importer were wrong for some entries of the game's lock check (the check
  stalled). They were corrected: a copy of these games that stalls on the lock
  check should be imported again with the new version.
- **F9 / F10** put the default profile of player 1 / 2 into the running game in
  every game that supports profiles, also on a cabinet with a plain keyboard
  (:ref:`online_usb_section`). The Phoenix double login was fixed.
- **Real AM.PASS readers** work in Prime 2, XX and Phoenix: reader 1 is player
  1 and reader 2 is player 2 (:ref:`online_usb_section`).
- The USB profile stick of **NX2 and later** is kept in until you remove it
  (NX2 unmounts it after reading; the save is now written).

Web (the cabinet's pages)
-------------------------

- All pages, and the profile pages of the old games, were redone in the
  project designer's design.
- The **live pages** (live scores, now playing, pads) are **on by default**;
  pressing the pads from the web stays off (:ref:`online_streaming_section`).
- **Settings page** ``/settings/``: normal and dangerous settings, one
  **operator key** for everything that changes the machine, a change log, and a
  lock-out against guessing (:ref:`online_settings_page_section`).
- **Insert as P1 / P2**: put any profile of the machine into the running game,
  with an **IN GAME P1/P2** badge on the home page; a side that is already
  taken is refused.
- Offline machines no longer offer online matching
  (:ref:`online_matching_section`).

Cabinet tools and the importer
------------------------------

- **Game transfer between two disks** of 2.0.0 (*experimental*,
  :doc:`importer/imperfect`): both licenses must be paid.
- Imported games whose key files were wrong (see the NX2 note above) are fixed
  for new imports.

Security and licensing
----------------------

- The license is now installed only from the **USB System Registration** entry
  (the menu no longer takes a license by itself at start-up) and the menu
  restarts after installing one.
- Everything the menu runs is checked against signed lists, and the update
  package is signed with a new key (:ref:`security_section`).

Known limits / not tested on real hardware
------------------------------------------

The 2.0.0 builds were tested in a virtual machine with all 32 game entries
(picture, sound, no crash), plus hand tests. These were **not** covered and may
need a real cabinet:

- **NX2 credit save** with a stick on real hardware.
- **F9 / F10 in Fiesta EX, Fiesta 2 and the Chinese builds**: the key reaches
  the game, but the full flow was tried on NX2 and Phoenix only.
- A **real AM.PASS reader** on a cabinet (the pass-through was tested with a
  simulated reader).
- **MK5 Prex 3 and Premiere 3** on a real cabinet.
- **Game transfer between disks**: experimental, not run end to end on real
  disks.
- **Phoenix 2.13** autoplay, and the autoplay of a whole song with holds in 2nd.
- **Prime Japanese Edition**: the shipped key file is not covered by the key
  check.
- **Exceed 2** and **NX2** each died or blacked out once in about
  nine virtual boots and were not reproduced; keep an eye on them.
- Everything that depends on the graphics card of a real cabinet (NVIDIA,
  Intel, AMD): for example the line at texture edges in the old games.
