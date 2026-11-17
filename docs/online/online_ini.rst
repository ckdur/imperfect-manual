.. _online_online_ini_section:

Reference: online.ini
~~~~~~~~~~~~~~~~~~~~~

**Where:** ``/SETTINGS/online.ini`` (:ref:`online_files_section`). Written
with the defaults below the first time Prime, Prime 2, XX or Phoenix starts;
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
and the next one player 2. How to find the port names:
:ref:`online_usb_ports_section`.
