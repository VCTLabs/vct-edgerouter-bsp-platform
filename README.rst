==============================
 VCT Beagleboard BSP Manifest
==============================

The various branches (other than this one) available here will configure the repo build
for the appropriate branches in each repository and clone them in the typical fashion,
ie, with either poky or oe-core as the parent directory and the additional metadata
layers underneath (as documented in the upstream setup).

The 2 main choices are:

1) The yocto BSP (and poky reference distribution) with meta-openembedded metadata
   plus (optional) TI and begalboard.org BSP's and meta-small-arm-extra

2) The openembedded-core metadata with choice of TI and begalboard.org BSP's, plus
   meta-openembedded metadata and meta-small-arm-extra for additional recipes

There are 3 main branches for each of the above choices: fido, jethro, and master.
Select the build branches and BSP/metadata using the respective branches in this
repo as shown below.  The branch you select with "repo init" will checkout the
corresponding branch HEAD commits on the configured branch for each repository.

See the default.xml file for repo and branch details.

Install the repo utility
------------------------

::

  $ mkdir ~/bin
  $ curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
  $ chmod a+x ~/bin/repo

Download the BSP source
-----------------------

::

  $ PATH=${PATH}:~/bin
  $ mkdir beagleboard-bsp
  $ cd beagleboard-bsp
  $ repo init -u https://github.com/VCTLabs/vct-beagleboard-bsp-platform -b poky-fido
  $ repo sync

At the end of the above commands you have all the metadata you need to start
building with poky and meta-oe on fido branches.

To start a simple image build::

  $ cd poky
  $ source ./oe-init-build-env build-dir  # you choose name of build-dir
  $ ${EDITOR} conf/local.conf             # set MACHINE to beaglebone
  $ bitbake core-image-minimal

You can use any directory (build-dir above) to host your build. The above commands will build an image for beaglebone using the core yocto BSP machine config and the default yocto-linux kernel. You can replace the default BSP config with either meta-ti or the meta-beagleboard BSP. This will provide a more Beagle-centric set of defaults for kernel and bootloader, as well as a bigger selection of kernels and TI support tools.

The main source code is checked out in the bsp dir above, and the build dir will default
to poky/build-dir unless you choose a different path above.

Source code
-----------

Download the manifest source here::

  $ git clone https://github.com/VCTLabs/vct-beagleboard-bsp-platform

Using Development and Testing Branches
--------------------------------------

Replace the repo init command above with one of the following:

For developers - jethro

::

  $ repo init -u https://github.com/VCTLabs/vct-beagleboard-bsp-platform -b poky-jethro

For intrepid developers and testers - master

Patches are typically merged into master-next and then are merged into master
after a testing and comment period. It’s possible that master has
something you want or need.  But it’s also possible that using master
breaks something that was working before.  Use with caution.

::

  $ repo init -u https://github.com/VCTLabs/vct-beagleboard-bsp-platform -b poky-fido


