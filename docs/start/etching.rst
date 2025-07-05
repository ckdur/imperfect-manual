Etching the Imperfect Collection
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In this section, you will write (etch) the *Imperfect Collection* image onto a
hard disk. The image file is provided in a compressed `.img.gz` format, which
needs to be decompressed and written as a raw disk image.

.. warning::

   **Data loss warning**: Etching the image will completely erase all existing
   data on the target disk. Double-check the device you are writing to before
   proceeding.

Downloading
-----------

Originally the downloading is in the public website of 
`NTDEC/Imperfect  <https://ntdec.net/imperfect>`_ but probably the demo graphics
are a little annoying. We provide the images in the following mega links:

- **Image folder** `Download here <https://mega.nz/folder/5UZDCbgL#Mti4JBk3kv4G-uXk1v5YLw>`_
- **Updates** `Download here <https://mega.nz/folder/ZUBVhAhZ#-a9nsLkCC9-zY7uSO8apfA>`_

Download the version of preference from the *Image Folder*. We recommend
downloading the latest version provided. If an inferior version was downloaded,
you can upgrade the system by downloading the updates. Go to the section :ref:`updates_section`
for further information.

Linux
-----

On Linux, etching the image is straightforward using standard command-line
tools:

1. Insert the target hard disk and identify its device path (for example, 
   `/dev/sdX`). You can check this using the `lsblk` or `fdisk -l` commands.
2. Run the following command, replacing `/dev/sdX` with your target disk:

   .. code-block:: bash

      gunzip -c imperfect_collection_vX.X.X_RELEASE.img.gz | sudo dd of=/dev/sdX bs=4M status=progress

3. Wait until the process completes. You will see the transfer progress if using
   `status=progress`. Once finished, safely eject the disk.

Windows
-------

On Windows, you can use popular imaging tools to write the `.img.gz` file to the
disk. Two recommended options are:

- **balenaEtcher** (https://etcher.io): A simple graphical tool that supports 
  compressed images directly.
- **Rufus** (https://rufus.ie): If using Rufus, you need to first extract 
  `imperfect_collection_vX.X.X_RELEASE.img.gz` using a program like 7-Zip to
  obtain the raw `.img` file.

**Using balenaEtcher:**

1. Download and install balenaEtcher.
2. Open Etcher, click *Flash from file*, and select `imperfect_collection_vX.X.X_RELEASE.img.gz`.
3. Select your target hard disk.
4. Click *Flash* and wait for the process to complete.

**Using Rufus:**

1. Extract `imperfect_collection_vX.X.X_RELEASE.img.gz` using 7-Zip to get `imperfect_collection_vX.X.X_RELEASE.img`.
2. Open Rufus.
3. Under *Boot selection*, click *SELECT* and choose the extracted `imperfect_collection_vX.X.X_RELEASE.img`.
4. Ensure the target disk is selected correctly.
5. Click *START* to begin writing.

macOS
-----

On macOS, while balenaEtcher is the recommended method due to its simplicity and
compatibility, you can also use command-line tools similar to Linux.

**Using balenaEtcher:**

1. Download and install balenaEtcher for macOS from https://etcher.io.
2. Open Etcher, click *Flash from file*, and select `imperfect_collection_vX.X.X_RELEASE.img.gz`.
3. Select your target disk.
4. Click *Flash* and wait for completion.

**Using the Terminal (Advanced Users):**

If you prefer using the Terminal:

1. Insert your target disk and identify its device name using:

   .. code-block:: bash

      diskutil list

2. Unmount the disk:

   .. code-block:: bash

      diskutil unmountDisk /dev/diskX

   Replace `diskX` with your target disk identifier (e.g., `disk2`).

3. Etch the image:

   .. code-block:: bash

      gunzip -c imperfect_collection_vX.X.X_RELEASE.img.gz | sudo dd of=/dev/rdiskX bs=4m

   Using `/dev/rdiskX` instead of `/dev/diskX` improves write speed.

4. Once done, eject the disk safely:

   .. code-block:: bash

      diskutil eject /dev/diskX

-----

After completing this step, your hard disk will contain the *Imperfect
Collection* loader and is ready for use in your MK hardware. Proceed to the next
section to install it into the machine and begin the boot process.
