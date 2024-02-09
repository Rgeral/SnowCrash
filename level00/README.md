# SnowCrash Level 00

## Introduction
Welcome to SnowCrash Level 00! In this level, we encountered some challenges but eventually found the solution to proceed further.

## Initial Confusion
At the beginning of this level, we faced some confusion about what to do next. We sought guidance from a peer who had completed the project before. They suggested looking for 'flag00' to proceed.

## Searching for 'flag00'
We initiated a search using the 'find' command to locate 'flag00'. However, the command 'find / -user flag00' returned an unreadable output filled with 'permission denied' errors.

## Finding a Solution
After some research, we discovered a simple solution: redirecting the error output to /dev/null, acting as a 'trash can'. The command 'find / -user flag00 2> /dev/null' resolved the issue.

## Discovering the Password
Using the modified command, we found two files containing a password: 'cdiiddwpgswtgy'. Unfortunately, this password didn't work to proceed to the next level.

## Decryption Process
We explored options to decrypt the password and came across a Caesar cipher decryption tool at [dCode](https://www.dcode.fr/chiffre-cesar). The tool revealed the decrypted password: 'nottohardhere'.

## Final Steps
Armed with the correct password, we successfully accessed the next level:
```bash
flag00@SnowCrash:~$ getflag
Check flag. Here is your token: nottohardhere
