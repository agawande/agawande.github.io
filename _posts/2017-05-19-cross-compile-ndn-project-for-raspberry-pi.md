---
layout: post
title:  "Cross compile"
date:   2017-05-19 18:59:09 -0500
categories: NDN RaspberryPi Cross-compile
published: false
---


0) mkdir cross-compile; cd cross-compile

1) git clone --depth 1 https://github.com/crosstool-ng/crosstool-ng

2) mkdir ct-ng-bin

3) cd crosstool-ng

4) ./bootstrap (only needed if downloading from crosstool-ng)

5) ./configure --prefix=/home/ashlesh/Projects/cross-compile/ct-ng-bin

   (./configure --enable-local)

sudo apt-get install gperf bison flex libncurses5-dev
6) make -j4

7) ./ct-ng armv6-rpi-linux-gnueabi

8) ./ct-ng build

Will take a long time

9) x-tools is in HOME folder

Yes, it's possible. Run ct-ng like this

CT_DEBUG_CT_SAVE_STEPS=1 ct-ng build
After crashing at a certain step, just find the step in the list produced by

ct-ng list-steps
At which point you can resume the build by running

RESTART=libc_start_files ct-ng build

68:53 - gdb, cross-gdb, gdbserver were built extra


Compile time of raspberry pi 2 (ARMv7 Processor rev 5) for ndn-cxx using clang++-3.9: 20m57.476s

sudo apt-get update
sudo apt-get install git
ndn-cxx
sudo apt-get install clang-3.9
sudo apt-get install libssl-dev
sudo apt-get install libcrypto++-dev
sudo apt-get install libsqlite3-dev
sudo apt-get install libboost1.55-all-dev
CXX=clang++-3.9 ./waf configure --boost-libs=/usr/lib/arm-linux-gnueabihf/

NFD
sudo apt-get install pkg-config
sudo apt-get install libpcap-dev
CXX=clang++-3.9 ./waf configure --boost-libs=/usr/lib/arm-linux-gnueabihf/ --without-websocket
19m44.141s

------

With provided tools

sudo apt-get install zlib1g:i386

