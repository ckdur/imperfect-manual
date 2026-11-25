.. _licensing_section:

Licensing
---------

Purpose of Licensing
^^^^^^^^^^^^^^^^^^^^

The *Imperfect Collection* loader includes a built-in **licensing system**
originally designed as its revenue source. Although the project is now intended
to be provided **free of charge** only relying on donations, the licensing 
mechanism remains active to preserve its **unique registration structure** and
ensure:

- Each copy of Imperfect Collection remains **unique and traceable**.
- **Game transference** between separate copies is prevented, avoiding
  unauthorized distribution of game files. The only exception is the
  :doc:`transfer between two paid 2.0.0 disks <../importer/imperfect>`
  (experimental).

- The loader continues serving its archival purpose **without enabling piracy**.

This approach respects the intellectual property of the original games while
allowing preservation and enjoyment within each licensed machine.

Licensing Procedure
^^^^^^^^^^^^^^^^^^^

To license your Imperfect Collection installation, follow these steps.

1. **Gather Required Information**

   You will need:

   - A **Name**: up to **20 characters long** (letters, numbers, or simple symbols). 
     This will be shown as the license holder’s name.

   - The **Hard Disk Serial Number**, which is:

     - Displayed in the loader’s main menu footer.  
     - Printed on the actual hard disk label (e.g., Toshiba MQ01ABD100, Serial **123456789**).

   .. note::

      If you are unable to locate or read the serial number directly, the system
      provides an alternative method described below.

2. **Creating a License Request File**

   If you do not have a valid license file yet:

   - Insert a **USB stick formatted in FAT32** into the MK machine.
   - Access the **Settings menu** by pressing the Service button.
   - Select **USB System Registration**.

   The system will generate a file named **`request.txt`** on your USB stick.
   This file contains all necessary registration details.

3. **Submitting Your Request**

   - Send the generated `request.txt` file to NTDEC if you are supporting.
     (site: `ckdur Patreon <https://patreon.com/ckdur>`_)

   - For free users, please go directly to `http://ntdec.net:8080/ <http://ntdec.net:8080/>`_ .
     Put the serial (From the screen or the `request.txt`) and a name of maximum
     20 characters. If you put more than 20 characters, will be truncated.
  
  .. warning::
    The information will be registered. If concerned about your privacy, please
    note that we use this information as statistics.

4. **Receiving Your License File**

   After processing your request, you will receive a file. Rename the file to 
   **`license.txt`**.

5. **Installing the License**

   - Place the received `license.txt` into the root of a **FAT32-formatted USB stick**.
   - Insert the USB stick into the MK machine.
   - Go to the **Settings menu** and select **USB System Registration** again.

6. **Verification**

   After successful registration:

   - The system will display your chosen **Name** in place of “UNLICENSED”.
   - The **“By”** field will update to show the licenser name (e.g., **NTDEC**).

   This confirms that your installation is now licensed and fully operational.

Re-Licensing Warning
^^^^^^^^^^^^^^^^^^^^

.. warning::
    If you choose to **re-license your system** using a different `license.txt`
    file (for example, to change the name or migrate licenses, or use another hard disk):

    - **There is a risk of losing all installed games and settings.**
    - This will **force a complete reinstallation** and re-import of all game data.

    Only perform re-licensing if absolutely necessary, and ensure you have backed
    up all critical data before proceeding.

There are special licenses that allow the migration of data totally safe between
hard disks, but those are locked behind **donation percs**. If you choose to
support us, this feature will be available.

.. _license_import_section:

Importing games needs a license made for this disk
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Since 2.0.0 a license does two things, and they do not depend on the same
data:

- It **licenses the machine**: your name appears in the menu and the games
  that are installed can run. This part is tied to the machine, so a
  ``license.txt`` you kept keeps working on that machine.
- It **allows the machine to import games** (the *Game Transfer* feature).
  This part is tied to an *import key* that the system creates on the disk the
  first time you make a ``request.txt``. The license you get back carries a
  certificate for that key.

The import key lives on the disk, in the SETTINGS partition. **Writing the
image to the disk again creates a new disk with no import key**, so the
``license.txt`` of the previous installation still licenses the machine but
can no longer import:

- the menu shows your name as usual;
- the importer stops at once with::

     This machine cannot sign imported games: ...
     Use "Relicense" in the menu: it writes request.txt to the USB
     drive; the license you get back carries the import certificate.

What the message calls "Relicense" is the **USB System Registration** entry
of the Settings menu.

What to do: on the newly written disk, make a **new** ``request.txt`` (step 2
above), send it to your licenser and install the ``license.txt`` you get back.
Do this before you plan an import session. Copying an older ``license.txt``
again does not help.

Keeping the import key (no new license needed)
""""""""""""""""""""""""""""""""""""""""""""""

If you know that you are going to write the disk again, you can skip the round
trip with your licenser: the import key is one small file,
``/SETTINGS/import.key`` (:ref:`how to reach the SETTINGS partition
<online_files_settings_section>`).

1. **Before** writing the disk, copy ``import.key`` out of its SETTINGS
   partition and keep it together with your ``license.txt``.
2. After writing the disk and letting it boot once, put ``import.key`` back
   into the SETTINGS partition of the new disk.
3. Install your ``license.txt`` as usual. The order of steps 2 and 3 does not
   matter.

The license you already have then imports again. The key only fits the
machine and the license it was made for.

.. note::

   Updating a machine with **USB Update** does not touch the SETTINGS
   partition: the import key stays, and the license you have keeps importing.
   Only writing the whole image again loses it.

.. _license_migration_section:

License migration (2.0.0 and later)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Version 2.0.0 hardened the licensing system: licenser keys are pinned, update
packages are signed, and a license is bound to a **machine fingerprint** rather
than only to the hard disk serial number.

- Licenses issued by older versions (bound to the disk serial) are still
  **read and trusted**, and are **migrated on the machine** to the new binding.
  You do not need to request a new license when upgrading.
- Licenses from every historical licenser key generation remain valid.
- Disks with a short serial number are now licensed correctly.
- When a game supports it, the AM.PASS reader configuration is generated from
  the license.

^^^^^

By completing this process, you ensure your loader operates under its intended
preservation framework while respecting the anti-piracy measures that protect
these historic titles.
