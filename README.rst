VCT Beagleboard BSP startup
===========================

To get the BSP you need to have repo installed and use it as:

Install the repo utility
------------------------

  $ mkdir ~/bin
  $ curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
  $ chmod a+x ~/bin/repo

Download the BSP source
-----------------------

  $ PATH=${PATH}:~/bin
  $ mkdir beagleboard-bsp
  $ cd beagleboard-bsp
  $ repo init -u https://github.com/VCTLabs/vct-beagleboard-bsp-platform -b jethro
  $ repo sync

At the end of the commands you have every metadata you need to start work with.

To start a simple image build:

  $ cd poky
  $ source ./oe-init-build-env build-dir
  $ bitbake core-image-minimal

You can use any directory to host your build.

The main source code is checked out in the poky dir above, and within poky
as well.  See the default.xml file for details.

Contributing
------------

To contribute to this layer you should send the patches for review to the
mailing list.

Source code
-----------

    https://github.com/VCTLabs/beagleboard-bsp-platform

When creating patches, please use something like:

  $ git format-patch -s --subject-prefix='vct-beagleboard-bsp-platform][PATCH' origin

When sending patches, please use something like:

  $ git send-email --to answers@vctlabs.com <generated patch>

Using Development and Testing Branches
--------------------------------------

Replace the repo init command above with one of the following:

For developers - master

  $ repo init -u https://github.com/VCTLabs/vct-beagleboard-bsp-platform -b master

For intrepid developers and testers - master-next

Patches are typically merged into master-next and then are merged into master
after a testing and comment period. It’s possible that master-next has
something you want or need.  But it’s also possible that using master-next
breaks something that was working before.  Use with caution.

  $ repo init -u https://github.com/VCTLabs/vct-beagleboard-bsp-platform -b master-next

