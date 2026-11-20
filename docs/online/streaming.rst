.. _online_streaming_section:

Live pages for streamers
~~~~~~~~~~~~~~~~~~~~~~~~

The cabinet can show, on its own web page, what is being played right now:
the game, the song and chart, the players, the score of the last songs, the
**scores of an online match on both machines** and the **pad presses** with
the lights. The pages update by themselves and are made to be put on a stream
as a browser source (OBS and similar programs).

They are **off** until the operator turns them on: ``enabled=1`` in the
``[stream]`` section of ``/SETTINGS/online.ini``
(:ref:`online_stream_ini_section`).

The pages
---------

Open them from a PC or phone on the same network as the cabinet, at the
address of the Profile manager (the F8 QR code) followed by:

``/live/``
  Everything on one page.

``/live/overlay.html``
  The same with a transparent background, for a browser source. Options in
  the address: ``?show=song,match,scores,pads`` (what to draw, in any
  combination), ``&scale=1.5`` (bigger text), ``&bg=dark`` (a background).

``/live/pads.html``
  The two pads as the old broadcaster (``broadcaster.py``) drew them, with
  nothing to install: the colour of a panel is its **light**, the four thin
  bars around it are its four **sensors** (left, top, right, bottom; white
  while pressed), a white outline means the panel is pressed, and a row shows
  the cabinet lamps L2S, L1N, NEON, L1S and L2N and the game's name. When
  pressing is on, a *Take control* button lets the operator press (see below).
  For OBS use ``/live/overlay.html?show=pads``, which never presses.

``/api/live`` and ``/api/live/stream``
  The same data as JSON, and as a live stream (Server-Sent Events), for
  your own overlays.

What is shown
-------------

**Game** and **song**: the game that runs, and the song as it is loaded,
with its banner, artist and chart (single or double and the level). For
NX2 up to Phoenix. During the song select the song under the cursor is shown
where the game lets it be seen. UCS charts of XX and Phoenix show the file
name. Zero, NX, Exceed, Exceed 2, PMod and the CD-era games (1st to Premiere 3 / Prex 3) show the song too
(no banner; 1st and 2nd have no titles, and their HOW TO PLAY shows as a song).

**Score while playing and at the end of each song**, for the games that do
not use the network: Zero, NX, NX2, NXA, Fiesta, Fiesta EX and Fiesta 2 (with or
without a USB stick), Exceed and Exceed 2, PMod, and the CD-era games (their score only). At the end of every
song the page lists the player's score, grade, judgements and max combo
(a stage break shows as FAILED); while the song plays, the running score.

**Online match** (XX and Phoenix): both players (the one on this machine and
the opponent on the other machine), the chart both play, the live combo or
miss counter of each side while they play, and both results at the end, with
the winner.

**Players and scores** of the network games (Prime to Phoenix): the names that
logged in and the last scores.

Pressing from the page (operator)
---------------------------------

Like the old broadcaster, the pads page can also press: the panels of both
pads (click, or touch with several fingers at once; a panel stays down while
it is held), a single sensor by its bar, and the buttons SERVICE, TEST, COIN1,
COIN2 and CLEAR. With keyboard input turned on for the cabinet
(``/SETTINGS/.keyboard``), also the keys **Q E S Z C** (player 1) and
**R Y G V N** (player 2) of the PC's keyboard and 1 to 5 for the buttons.
Pressing a single sensor needs a system version from 2026-11-19 on; older ones
press the whole panel only.

This controls the machine, so it is separate from the streaming switch and
off by default: set ``press=1`` **and** an operator key ``press_key=...`` in
the ``[stream]`` section (:ref:`online_stream_ini_section`). Open
``/live/pads.html``, press *Take control* and type the key. The page shows
*IN CONTROL* with a gold frame while it has control.

- Only one device at a time has control. Another one is refused until the
  first gives it back or goes silent.
- Nothing stays pressed: everything is let go when the page loses focus, is
  hidden or closed, or when the machine hears nothing from it for 1.5
  seconds (for example a lost Wi-Fi connection).
- The live pages and the OBS overlay never press (``/live/`` can only switch
  autoplay, see below).

Autoplay from the page (operator)
---------------------------------

Autoplay is switched from the live pages, not from the menu: ``/live/`` and
``/live/pads.html`` show an **Autoplay** button while the running game has an
autoplay the machine can switch. It needs the same settings and key as
pressing (``press=1`` and ``press_key=...``): type the key and press
*Autoplay: OFF (turn on)*. The game then plays the steps by itself, for both
players.

- **Games**: the CD-era games from O.B.G. to Premiere 3 / Prex 3, Exceed,
  Exceed 2, Zero, NX, NX2, NXA, Fiesta, Fiesta EX, Fiesta 2, Prime, Prime 2
  and XX. Not 1st and 2nd, Infinity, Phoenix or PMod: the button does not show
  there.
- It stays on only **while the page that turned it on stays open**: closing
  that page (or losing its connection for a few seconds) turns it off, and so
  does leaving the game or starting another one. Any device with the key can
  turn it off.
- While it is on, every live page and the OBS overlay show **AUTOPLAY**, and
  the scores of songs played with autoplay are marked **AUTO**, so a stream
  never shows them as a real play.
- The game still keeps those scores as usual (in the player's save or
  profile): the mark is only on the live pages.
- It needs a system version from 2026-11-20 on.

What is public
--------------

With ``enabled=1`` **anyone on the network of the cabinet** can open these
pages, like the Profile manager. They show player names, including the name of
an online opponent from another place (the same name the cabinet shows on its
screen during the match). Use ``names=0`` to hide the names and ``pads=0``
to hide the pads. Nothing of this leaves the cabinet: the pages are served by
the cabinet itself, never by a server on the internet.
