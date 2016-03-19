# Jeremy's Cats (650)

## Problem

> J.T. !!!! DON'T DELETE THAT GUY!! OH NO, WHAT WAS HIS PASSWORD??!  
> ps, try harder.  
> http://104.131.43.243:8080/

## Solution

We see immediately that the server is running Apache Tomcat, and clicking on the manager link and guessing some passwords reveals that the username is `admin` and the password is `password`. We create a .war file with an `index.jsp` containing some basic Java code to run a shell command specified by a GET parameter and poke around. We see that there is a `/flag.txt` on the server owned by root, but we don't have free `sudo` access like in Robert Tables. We look for other `setuid` (can run as file owner) binaries owned by root using `find / -perms 4000 -user root` and find a suspicious binary called `moar` in `/bin`. Running it reveals that it runs the `cat` command, which makes it seem useless, but since we know its `setuid`, we try it on `/flag.txt`: `moar /flag.txt` and get the flag.

## Flag
`flag{really_gud_password_but_wait_theres_moar}`
