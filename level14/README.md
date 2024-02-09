# SnowCrash Level 14

## Introduction
Here we have nothing to interact with. After minutes of thinking, we asked ourselves, "Should we analyze Getflag?" We put Getflag in Ghidra and found that the code to decrypt all the flags was `ft_des`, so we just put the last encrypted token from Level 13 in our code, and we got the flag.

## Obtaining the Token
After running our decryption code:

level14@SnowCrash:/bin$ su flag14
Password: 7QiHafiNa3HVozsaXkawuYrTstxbpABHD8CPnHJ

flag14@SnowCrash:~$ getflag
Check flag. Here is your token: 7QiHafiNa3HVozsaXkawuYrTstxbpABHD8CPnHJ

