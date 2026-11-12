.. _security_section:

The signed boot chain
~~~~~~~~~~~~~~~~~~~~~

Since 2.0.0 every stage of the boot checks the next one. All checks use **one
key**: the update-signing key. Its public half is pinned in ``ntdecsig.c``
(grub), ``sigcheck.c`` (konnichiwa), ``encrypt_exe.c`` and
``menugl/authority.c``; rotating the key means changing all four.

grub to kernel
^^^^^^^^^^^^^^

The ``ntdecsig`` grub verifier is built into ``core.img`` and boots only kernels
that end with a valid ed25519 trailer (``kernel | sig[64] | "NTDECSIG.KERNEL1"``),
halting with *Boot halted* otherwise. It refuses modules from ``/boot/grub`` and
every other file type, except ``grubenv`` and the deliberate one-shot "boot the
other disk" chainload. The build signs ``bzImage.phoenix.enc`` right after it is
encrypted. A kernel copied to the BOOT partition without the trailer leaves the
machine unbootable.

RELEASE kernels also set ``CONFIG_CMDLINE_OVERRIDE`` and ignore grub's kernel
arguments; debug kernels still accept ``-append``.

konnichiwa to disk
^^^^^^^^^^^^^^^^^^

konnichiwa runs inside the signed kernel. It runs the menu (``glmenuos``,
``glmenuos.sh``), ``importer32``, ``pmod-release``, ``pmod.sh`` and the SETTINGS
backup menus only if they match a detached ``<file>.sig``, and it runs the
checked copy from ``/tmp``. The disk scripts and the update package ship the
signatures. Anything that changes one of these files on a disk must re-sign it.

OS images (dm-verity)
^^^^^^^^^^^^^^^^^^^^^

The base OS image (``u``, mounted on ``/usr``) and the per-GPU driver image (on
``/usr/lib``) mount only as dm-verity volumes. The build appends the hash tree
and a signed 4 KiB trailer (name, root hash, salt) to every image, so the disk
scripts and the update carry signed images. The kernel restarts the machine on a
corrupted block.

An update never overwrites a mounted image: it writes ``fs/<l>.ntdec.new`` and
konnichiwa renames those into place on the next boot, before mounting.

Fail closed
^^^^^^^^^^^

Any check that fails (an image, the menu, ``glmenuos.sh``, ``importer32``,
``pmod-release``, ``pmod.sh``) restarts the machine; nothing falls back to an
unchecked start. The console importer request file ``/tmp/cli.sh`` is never run:
konnichiwa takes only its region value and re-checks ``importer32`` before
running it. Release images, PMOD included, start no telnet.

Limits
^^^^^^

On these BIOS machines nothing protects the MBR or ``core.img`` itself; whoever
can write the disk can replace grub.
