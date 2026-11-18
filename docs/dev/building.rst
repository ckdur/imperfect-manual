Building the loader
~~~~~~~~~~~~~~~~~~~

The *Imperfect Collection* multiloader is a bootable disk image that chain-loads
many *Pump It Up* releases behind a GL menu, with a licensing layer. Most of the
interesting parts are git submodules of the main repository (``cpio_trap`` for
the boot chain, menu and disk tooling; ``elfloader``; ``pki``; ``grub``;
``mk3_linux_ports``; ``PMOD`` and ``PMODTHEME`` for the PMOD simulator and its
theme/game data; ``dongle``; and others).

.. note::

   The ``PMOD`` and ``PMODTHEME`` submodules used to be called ``SaninetAll`` and
   ``saninettheme``. See :ref:`migrating_checkout` if you have an older checkout.

Building
^^^^^^^^

.. code-block:: bash

   bash make_multiloader.sh      # debug make_all, then release make_all, then release make_pmod

``make_multiloader.sh`` runs ``make_all.sh`` twice (debug, then ``RELEASE=1``)
and then ``make_pmod.sh`` (``RELEASE=1``). Budget about **40-60 minutes**: both
i386 kernels are rebuilt from scratch twice, plus pmod and four disk images.

.. list-table::
   :header-rows: 1
   :widths: 30 70

   * - Directory
     - Key output
   * - ``build.multiloader.debug/``
     - ``imperfect_collection_v<VER>.img.gz`` + ``.qcow2``, ``imperfect_collection_deploy.zip``
   * - ``build.multiloader.release/``
     - ``imperfect_collection_v<VER>_RELEASE.img.gz`` + ``.qcow2``
   * - ``build.pmod.release/``
     - ``pmod6_arcade_v<VER>_RELEASE.img.gz`` / ``.qcow2`` (vfat), ``..._ext_...`` (ext2) and ``..._ntfs_...`` (NTFS, mounted by ntfs-3g over FUSE)

Each ``.qcow2`` is made with ``qemu-img convert`` from the raw intermediate image,
so it is about the size of the ``.gz``. To boot a build in a virtual machine:

.. code-block:: bash

   ./run_vm.sh            # release image, virgl; also: debug, --vga std, --vga cirrus

Prerequisites
^^^^^^^^^^^^^

No ``sudo`` is required.

- **Docker**, with your user in the ``docker`` group. The images used are
  ``ckdur/linux32-ckdur`` (the 32-bit build container, GCC 8.3.1) and
  ``ckdur/imperfect-diskbuilder`` (built automatically for the disk step).
- **Host packages**: ``gcc-12``, ``gcc``/``g++``, ``make``, ``node``/``npm``,
  ``zip``, ``cpio``, ``mksquashfs``, ``veritysetup`` (cryptsetup, for the
  dm-verity images), ``x86_64-w64-mingw32-gcc``, ``i686-linux-gnu-gcc``,
  ``qemu-img`` (and ``qemu-system-i386`` to boot the result), the development
  libraries for ``ftgl libusb-1.0 gl glu glew freetype2 fontconfig``, the Tcl
  headers, and ``autoconf``, ``automake``, ``libtool`` and ``gettext`` (the grub
  submodule is bootstrapped on the host).
- **Game data**, which is not in the repository, at a fixed path:
  ``/media/Extended/Games/PIU/plugin``. The PMOD content comes from the
  ``PMODTHEME`` submodule.
- **The update-signing key** ``pki/update_signing.key`` (secret, never
  committed). The build refuses to continue without it.

No Andamiro payloads are needed: the initramfs, the phoenix kernel and the base
``u`` OS image are all built from source.

The toolchain split
^^^^^^^^^^^^^^^^^^^

Recent distributions ship GCC 15 (C23 by default), which this project predates.
The rule that keeps the build working:

.. list-table::
   :header-rows: 1
   :widths: 40 20 40

   * - What compiles
     - Where
     - Compiler
   * - UPX, konnichiwa, squashfs, elfloader, dongle, importer, glmenuos/glmenu32, PMOD
     - in ``ckdur/linux32-ckdur``
     - plain ``gcc`` (8.3.1)
   * - the Linux kernels (4.19 / 5.15)
     - on the host
     - ``gcc-12`` (GCC 15 cannot build them: ``false``/``true``/``bool`` are C23 keywords)
   * - host userspace C (``pki/``, ``glmenu64``)
     - on the host
     - GCC 15 with ``-std=gnu17``

Rootless disk imaging
^^^^^^^^^^^^^^^^^^^^^

The final disk-image steps need block-level access (loop devices, partitioning,
LUKS, mkfs, mount, grub). Instead of host ``sudo`` they run inside a privileged
docker container. The GAME partition is LUKS1 opened by a raw master key with all
passphrase keyslots removed, so passphrase-only tools such as libguestfs cannot
open it.

Checking that the games run
^^^^^^^^^^^^^^^^^^^^^^^^^^^

``tools/vmtest/vmtest.sh all`` boots every game headless under QEMU/virgl and
judges each one; it needs an image with the game data installed. When something
looks wrong, read QEMU's stderr first: a guest GL context killed by the host is
reported nowhere else, and the game keeps running with audio on a frozen or
black screen.

The virgl image (``v``) uses Mesa 23.3 with DRI3 always on. Do not force DRI2
with ``LIBGL_DRI3_DISABLE``. ``libxshmfence`` must be configured with
``--with-shared-memory-dir=/tmp``, otherwise every DRI3 client silently gets no
back buffer.

.. _migrating_checkout:

Migrating a checkout from SaninetAll / saninettheme
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Pulling the rename does not remove the old folders, so you would have old and
new copies side by side. Either delete the old copies (after making sure they
hold no uncommitted work):

.. code-block:: bash

   git pull
   rm -rf SaninetAll saninettheme .git/modules/SaninetAll .git/modules/saninettheme
   git submodule sync && git submodule update --init --recursive

or move them into place to avoid re-cloning, after ``git pull`` and **before**
``git submodule update``:

.. code-block:: bash

   mv .git/modules/SaninetAll .git/modules/PMOD && mv SaninetAll PMOD
   mv .git/modules/saninettheme .git/modules/PMODTHEME && mv saninettheme PMODTHEME
   echo "gitdir: ../.git/modules/PMOD" > PMOD/.git
   echo "gitdir: ../.git/modules/PMODTHEME" > PMODTHEME/.git
   git -C .git/modules/PMOD config core.worktree ../../../PMOD
   git -C .git/modules/PMODTHEME config core.worktree ../../../PMODTHEME
   git submodule sync && git submodule update --init --recursive
