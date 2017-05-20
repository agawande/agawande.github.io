---
layout: post
title:  "Introduction to Mini-NDN"
date:   2017-05-19 18:59:09 -0500
categories: NDN Mini-NDN Mininet
---

[Mini-NDN][mini-ndn] is a [Mininet][mininet] based network emulator for [Named Data Networking][named-data].
Mininet provides `host` or `node` which are simply bash processes (Mininet also provides switches and controllers, but
they are not used in our project yet).
Each of the hosts has its own networking stack. This is done by using Linux network namespaces.
Virtual ethernet pairs are used for linking these hosts. Link parameters such as delays, loss, bandwidth etc. can be set on the links
Network namespaces are available only in Linux kernel. That is why Mininet can only be run only on Linux.
Since network namspaces are not available in userspace, Mininet needs to run as sudo. This is the response I got
on the Mininet mailing list about running without sudo from Bob Lantz (original author of Mininet) himself:

[https://mailman.stanford.edu/pipermail/mininet-discuss/2015-October/006549.html][mailinglist]

Mininet is mostly written in python and hence allows for rapid development with simple APIs.
Mini-NDN project started by forking Mini-CCNx which was a network emulator for PARC's Content Centric Network (CCNx).
[Mini-CCNx][mini-ccnx] itself was a direct fork of Mininet. It provided the functionality to provide a topology file
and created a network in Mininet. In this network CCNx forwarder is run on each node. Mini-CCNx also inherited Mininet's GUI,
Mininetedit as Miniccnxedit.

Mini-NDN uses the same basic framework introduced in Mini-CCNx to connect nodes together directly with each other using virtual ethernet pairs
(as opposed to connecting nodes to switched as done in Mininet examples). One hack was to set consecutive IPs on the two virtual ethernets so
that they can ping each other. The following figure illustrates this:

{:refdef: style="text-align: center;"}
![Mini-NDN explain]({{ site.url }}/assets/minindn-explain.png){:height="300px" width="500px"}
{: refdef}

Since then following changes have been made in Mini-NDN project:

- Mini-NDN runs NFD (NDN Forwarder) and NLSR (Routing protocol) on each node
- Mininet is now a dependency for Mini-NDN, forked code of Mininet is removed
- Mini-NDN config file supports NFD and NLSR options
- There is an experimental framework to write experiments
- Mini-NDN uses Mininet cluster edition to provide cluster functionality
- Minindnedit now supports NFD and NLSR parameteres in the GUI

I like to describe Mini-NDN as a bunch of python scripts to run multiple NFD and NLSR on a single machine.
Since a single machine can only handle so many processes there is a limit to scaling proportional to the CPU power
of the machine. That is why we developed the cluster edition to help with scaling.
But Mini-NDN provides a very realistic way to develop and test applications to run over NFD. Since applications
interact directly with unmodified versions of NFD. Furthermore, Mininet's command line allows interactive
communication with any process (ex: NFD) running on any node. One downside of emulation as opposed to simulation is
that it takes real time and hence is slower.

[named-data]: https://named-data.net
[mini-ndn]: https://github.com/named-data/mini-ndn
[mininet]: https://github.com/mininet/mininet
[mailinglist]: https://mailman.stanford.edu/pipermail/mininet-discuss/2015-October/006549.html
[mini-ccnx]: https://github.com/chesteve/mn-ccnx
