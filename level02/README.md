ls in /home/user/level02 : I fond level02.pcap
After some research i fond that level02.pcap could be open in Wireshark.
Then i tried to understand how i could find some informations to get the flag.

I tried to follow the TCP Stream and i fond some informations : 

/*************************************************************\

Linux 2.6.38-8-generic-pae (::ffff:10.1.1.2) (pts/10)

..wwwbugs login: l.le.ev.ve.el.lX.X
..
Password: ft_wandr...NDRel.L0L
.
..
Login incorrect
wwwbugs login:

/*************************************************************\

then i just tried some password, and the one was : ft_waNDReL0L

In the VM : 
su flag02, put the password : ft_waNDReL0L => Success
getflag => Check flag.Here is my token : kooda2puivaav1idi4f57q8iq