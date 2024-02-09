# SnowCrash Level 13

## Introduction
For this stage, we received a `level13` executable that we can execute. We put it in Ghidra to get the program in C. We see that:
```
if (_Var1 != 0x1092) {
  _Var1 = getuid();
  printf("UID %d started us but we we expect %d\n",_Var1,0x1092);
                  /* WARNING: Subroutine does not return */
  exit(1);
}
uVar2 = ft_des("boe]!ai0FB@.:|L6l@A?>qJ}I");
printf("your token is %s\n",uVar2);
```
So, if our UID is `4242`, we get the token. We just copy/pasted the code, erased the if condition, and got this program that does the same encryption (`exploit.c`).

## Obtaining the Token
After running the exploit program:
```
flag13@SnowCrash:~$ ./exploit
Check flag. Here is your token: 2A31L79asukciNyi8uppkEuSx
```
