# SnowCrash Level 02

## Introduction
Welcome to SnowCrash Level 02! In this level, we discovered a PCAP file named 'level02.pcap' in the directory '/home/user/level02'. This file contained valuable information that helped us progress.

## Initial Discovery
Upon inspecting the contents of '/home/user/level02', we discovered the 'level02.pcap' file. After conducting research, we learned that PCAP files can be opened and analyzed using Wireshark, a powerful network protocol analyzer.

## Analyzing the PCAP File
Using Wireshark, we investigated the 'level02.pcap' file to uncover potential clues. We focused on examining the TCP stream to extract relevant information.

## Information Extracted from TCP Stream
Within the TCP stream, we discovered the following sequence of events:

Linux 2.6.38-8-generic-pae (::ffff:10.1.1.2) (pts/10)
..wwwbugs login: l.le.ev.ve.el.lX.X
..
Password: ft_wandr...NDRel.L0L
..
Login incorrect
wwwbugs login:

The ellipses represent deletion characters, indicating that the user initially typed 'ft_wandr', then deleted three characters, entered 'NDRel', deleted another character, and finally input 'L0L'. This led us to the potential password: 'ft_waNDReL0L'.

## Accessing the Next Level
Armed with the potential password, we attempted to elevate privileges by switching to the 'flag02' user using the 'su' command:

su flag02
Password: ft_waNDReL0L

Success! We gained access to the 'flag02' user account using the derived password.

## Obtaining the Flag
With access granted, we executed the 'getflag' command to retrieve the token:

flag02@SnowCrash:~$ getflag
Check flag. Here is your token: kooda2puivaav1idi4f57q8iq
