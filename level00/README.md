For this first level, I was a bit lost without knowing exactly what to do, so I asked a fellow student who had already done this project, and he told me to look for 'flag00.' After quite a bit of searching, I started using the 'find' command to locate 'flag00.' 
However, the result of the command 'find / -user flag00' was unreadable and filled with 'permission denied' errors.

I looked for a solution, and in the end, it was quite simple: redirecting the error output to /dev/null, which seems to act as a kind of 'trash can.' Here's the command: 'find / -user flag00 2> /dev/null'

With this, I found two files that provided some kind of password: 'cdiiddwpgswtgy.' 
However, this password didn't seem to work to advance to the next level, so I started looking into how to decrypt it.

I passed this password to ChatGPT, which mentioned a letter substitution (Cesar). I then visited a website that allowed decryption using this method, and I found the following result: 'nottohardhere.' That's the password!
