# Secure Stuff Happens (350)

## Problem

> Go ahead, try and brute force my SSH server! But be warned... I'm watching you....  
> Did you really think I'd use a combination that only an idiot would use on his luggage?  
> 162.243.0.171:22

## Solution

SSHing into the given IP/port using OpenSSH gives and error: `Received disconnect from 162.243.0.171 port 22:3: couldn't match all kex parts`. Googling this error reveals that the port we are given is actually serving a Kippo honeypot. Looking around, we find a piece of software called `kippo-graph` that displays statistics on the Kippo honeypot, and we guess that the admin `git clone`d it into `/var/www`, so we go to `162.243.0.171/kippo-graph`. The flag is under the "Kippo-Input" tab in the "all input commands" CSV.

## Flag

`flag{uh_huh_h0n3y}`
