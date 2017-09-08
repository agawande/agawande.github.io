---
layout: page
permalink: /hackmemphis17/
---

Hackmemphis 2017 Pitch for RIOT OS
======

Proposal to port/compile RIOT OS to ESP8266.
RIOT OS is a real time OS for IOT anf have been ported to
many boards including Arduino Uno.
We want to bring it to ESP8266 which is a popular WiFi chip
with more than plenty resources to run RIOT.
Those who came to NodeBots Day are already familiar with ESP.
D1 Mini contains ESP-12 chip (a variant of 8266).

**Resources:**

1. RIOT-OS
   * [Website](https://riot-os.org)
   * [Source](https://github.com/RIOT-OS/RIOT)
   * [Wiki](https://github.com/RIOT-OS/RIOT)
   * [Pull request for a device driver for using ESP as an attached device](https://github.com/RIOT-OS/RIOT/pull/5898)

2. ESP
   * [Flash firmware](https://wiki.wemos.cc/tutorials:get_started:revert_to_at_firmware)
   * [open SDK](https://github.com/pfalcon/esp-open-sdk)

3. Knowledge/Skill/Tools required:
   * Makefile (Compiling programs)
   * MCU programming (C)
   * Linux
   * Git

4. From the mailing list of RIOT OS:
   * [Relevant Discussion 1](https://lists.riot-os.org/pipermail/devel/2016-February/003396.html)
   * [Relevant Dicsussion 2](https://lists.riot-os.org/pipermail/devel/2016-April/003802.html)
   * 

**Goals:**

0. Compilation of RIOT OS framework with ESP open SDK
1. Run Hello World of RIOT OS on ESP
2. Use GPIO pins through RIOT

**Chllenges:**

1. Not very detailed documentation about RIOT OS porting.

**People:**

1. Looking for 3-4 to help me make the port a reality (More welcome if interested).

**Why:**

1. If successful it may help a lot of people trying to use RIOT on ESP 8266.
   This can end up being a very popular repository.

**From RIOT OS developers**:

"From what I read in the discussions,
I would assume that it shouldn't be too difficult (sic!) for a developer who
has some experience with low-level MCU programming and either has already a
good understanding of RIOT's architecture or is willing to read documentation."
