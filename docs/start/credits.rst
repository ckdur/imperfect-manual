.. _credits_section:

Credits and free play
---------------------

Since 2.0.0 the menu and the games share **one pool of credits**. A coin you
drop while the menu is on the screen is not lost when you start a game, and the
credits that are left when you leave a game are there for the next one.

How it works
^^^^^^^^^^^^

- **In the menu** a coin only counts as a coin: the menu has no price. The
  coins wait for the next game.
- **When a game starts**, a few seconds after it begins to run, the credits of
  the pool (and the coins dropped in the menu) are put into the game, at *that
  game's own price* (coins per credit).
- **While you play** the pool follows the game's whole credits. When the game
  ends, what is left stays in the pool.
- A **part of a credit** (for example 1 coin of a 2-coin credit) stays in the
  game and is lost with it. Only whole credits are kept.
- Credits above a game's limit (99, or the limit set in the game's own test
  menu) wait in the pool and go in as the game spends its own.
- The settings of each game (coins per credit, its own free play, its credit
  limit) are only **read**, never changed.
- A game that is in its **own free play** is left alone: it does not use the
  pool.
- The pool is saved after every change in two files, so a power cut at any
  moment leaves a usable copy and never costs more than the last change. Power
  cuts are the normal way to switch a cabinet off.

Which games share the pool
^^^^^^^^^^^^^^^^^^^^^^^^^^

All of them except the original **Exceed**, **Pro**, **Pro 2** and **PMod**:
1st, 2nd, O.B.G. and everything up to Prex 3, Exceed (mini), Exceed 2 (both
versions, including the Russian one), Zero, NX, NX2 (and the Chinese build),
NX Absolute (and the Chinese build), Fiesta, Fiesta EX, Fiesta 2, Prime, Prime
Japanese Edition, Prime 2, XX, Phoenix 2.12, Infinity and Pump Jump. For the
games that were imported or installed in other builds than the ones the loader
ships, the pool is simply not used and the game counts its own coins.

Prex 3, Premiere 3 and the other late MK3 games accept up to **99 credits**
(the original limit was 9).

Free play with the attract sequence
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When an old game is set to **free play** (or event mode) in its own test menu,
the original games kept the title screen up for ever and never ran the logo,
the intro movie and the demo play. Now the attract sequence runs as it does on
a machine with no credits, until somebody steps on the **center** panel: then
the title comes up and stays until a player starts, and the game shows
**FREE PLAY** and starts without spending a credit. Nothing needs to be
configured: it follows the game's own free play setting.

It is available in Perfect Collection, Premiere 1, Prex 1, Rebirth, Premiere 2,
Prex 2, Premiere 3, Prex 3, Exceed (mini) and both Exceed 2 versions. It is
*not* done for 1st, 2nd, O.B.G., O.B.G. SE, The Collection and Extra. From
Zero on the loader does not change the free play behaviour of the game (Prime
2, XX and Phoenix keep their title up by themselves).

Turning it off
^^^^^^^^^^^^^^

``/SETTINGS/credits.ini`` holds the pool. Setting ``enabled=0`` in its
``[options]`` section makes every game count its own coins again. The file is
rewritten by the machine all the time; if you edit it by hand, do it with the
machine off.

.. note::

   The pool is not shown by the menu yet. The credit counter you see is the
   one of the game that is running.
