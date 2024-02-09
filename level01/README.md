# SnowCrash Level 01

## Introduction
Welcome to SnowCrash Level 01! This level presented us with challenges in understanding where user passwords were stored on a Linux machine and how to decrypt them.

## Initial Investigation
Initially, we embarked on a search to locate where user passwords might be stored on a Linux machine. Our exploration led us to discover the files '/etc/shadow' and '/etc/passwd' (see the files in the resources provided).

## Discovering 'flag01' Line
Upon examining the contents of the files, we noticed that the 'flag01' line in '/etc/passwd' contained a different format, resembling a password. However, this password did not grant us access to the next level.

## Introduction to JohnTheRipper
During our research, we stumbled upon JohnTheRipper, a software designed for decrypting passwords. We learned that the string appearing in the '/etc/passwd' file was a hash, not a clear password. Historically, passwords were stored in this format before being replaced by "x" and stored in '/etc/shadow' (which we couldn't access).

## Decryption Process
We transferred the 'passwd' file to our local machine and utilized JohnTheRipper to decrypt it. Eventually, we obtained the password: 'abcdefg'.

## Final Steps
With the correct password in hand, we successfully accessed the next level:
```bash
flag01@SnowCrash:~$ getflag
Check flag. Here is your token: f2av5il02puano7naaf6adaaf
