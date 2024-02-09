# SnowCrash Level 03

## Introduction
Welcome to SnowCrash Level 03! In this level, we encountered a program named "level03" and embarked on a journey to understand its functionality and exploit it.

## Initial Exploration
Using the "ls" command, we listed the files in the directory and found a program named "level03." Upon using "cat" to view its contents, we realized it was in binary format, making it difficult to understand its workings.

## Disassembly and Analysis
To gain insight into the program's functionality, we attempted to disassemble it using 'objdump -d level03,' which provided an assembly program. However, the assembly code proved challenging to comprehend.

## Utilizing Ghidra
In our quest for understanding, we discovered Ghidra, a tool that can translate assembly code into C. After analyzing the code with Ghidra, we found the following "main" function in the program:

```c
int main(int argc, char **argv, char **envp)
{
    gid_t **rgid;
    uid_t **ruid;
    int iVar1;
    gid_t gid;
    uid_t uid;

    rgid = getegid();
    ruid = geteuid();
    setresgid(*rgid, *rgid, *rgid);
    setresuid(*ruid, *ruid, *ruid);
    iVar1 = system("/usr/bin/env echo Exploit me");
    return iVar1;
}
```

## Identifying the Exploitable Line

The line that caught our attention was: iVar1 = system("/usr/bin/env echo Exploit me");. It indicated that the program was calling the "echo" built-in, reminiscent of the Minishell project we had previously worked on.
Crafting the Exploit

Drawing from our experience with Minishell, where built-in commands were called using the 'PATH=' environment variable, we realized we might manipulate the program to call "getflag" instead of "echo."
## Execution and Success

To execute our exploit, we created a small program launching a new shell. Since the executable "level03" uses setuid and setgid, and the two "s" bits were set when doing ls -la:
```
-rwsr-sr-x 1 flag03 level03 8627 Mar 5 2016 level03
```
It meant that the code would run as flag03 and execute commands as flag03.

We exported the new PATH environment variable as follows: export PATH=/test:$PATH, and it worked! We are now in a new shell as flag03.
## Obtaining the Flag

With the newly acquired privileges, we executed the command:
```
flag03@SnowCrash:~$ getflag
Check flag. Here is your token: qi0maab88jeaj46qoumi7maus
```
