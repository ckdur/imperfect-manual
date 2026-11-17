.. _online_matching_section:

Online Matching
~~~~~~~~~~~~~~~

Online Matching exists in **XX** and **Phoenix**: two machines, anywhere, play
the same chart at the same time and compare results.

What you need
-------------

- The machine connected to the internet with a **network cable**. The address
  is taken automatically (DHCP). The game itself is still kept off the
  internet: only the match service can be reached.
- To be **logged in** (:ref:`online_login_section`) and **alone** on the
  machine: the mode is for one player per machine.

How to start a match
--------------------

1. Log in and reach song select.
2. Press the **upper-left** arrow: the channel list opens.
3. Move with the lower arrows to **ONLINE MATCHING** and press the centre
   step.
4. Pick a level range, then press the centre step three times.

The game now looks for another machine doing the same in the same game. When
it finds one, both screens show the two players (name, avatar, flag), and the
song, the result and the comparison follow by themselves. Each machine keeps
its own score in its player's profile.

To leave the search, press an upper arrow.

If the ONLINE MATCHING channel is missing
-----------------------------------------

The channel is only in the list while there is somebody to play against, that
is while the machine reaches the match service (or another machine, see
below). If it is not there:

- check the network cable;
- read ``/SETTINGS/piu_server.log``: it says ``match service online`` or why
  the service was not reached (:ref:`online_trouble_section`);
- remember that it needs exactly one player joined.

Playing between your own machines (LAN)
---------------------------------------

Several *Imperfect Collection* machines on the same network can share one
game server, with or without internet:

1. Choose one machine as the host and note its network address. Its
   ``online.ini`` stays as it is.
2. On every other machine, set ``lan_server=`` in ``/SETTINGS/online.ini`` to
   that address (:ref:`format <online_online_ini_section>`).
3. Start the same game on all of them. The host must be running the game too:
   its server only runs while a network game is up.

The profiles and the matching are then the host's: players log in on any of
the machines and are matched against each other. If the host also reaches the
internet, players from elsewhere join the same queue.

Two things follow from that on the machines that are not the host: they keep
no ``/SETTINGS/piu_server.log`` of their own (read the host's), and a USB
stick plugged into them is not read for the profiles of Prime 2, XX and
Phoenix, since the host only sees its own USB ports.
