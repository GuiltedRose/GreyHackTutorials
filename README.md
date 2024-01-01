# GreyHackTutorials
## NOTE: GreyHack is a video game. While this is mostly realistic, it DOES NOT reflect real hacks in any way; even if they are somewhat close (in few cases).

This is the public repo I created to help teach the game with the README. Note: the license doesn't apply it's just a good practice.

## Where to Start:

The tutorial is pretty easy if you follow the docs (manual).

Airmon allows us to go into a state known as "monitor mode" the default for all wirelss NICs is "managed mode" in the game this is as easy as this: `airmon start wlan0`.

## Cracking Wifi Passwords:

To crack passwords you need to use the airplay command. It is very straight forward as well: `airplay -b [BSSID] -e [ESSID]` the BSSID is a hexidecmal string, while the ESSID is the name of the network you are trying to connect to. Now you just wait (time will vary depending on the power variable).

The game manual recommends 7,000 ACKs (I will explain what this is soon). However, if it is a weak power you may need 20,000 ACKs. A good rule of thumb is either always wait for 20,000; or keep trying until you recieve the `file.cap`. Just writing this I got 20,473 ACKs.

The next tool we need to use to extract our wifi password is `aircrack` all it needs is the `file.cap`. By default it is located in the home directory in the file tree. so to use it we can either do: `aircrack /home/[username]/file.cap` or `aircrack file.cap` and it should say the following output if done correctly: `KEY FOUND! [password]` (if the game updates to allow ~/ instead of /home/user/ then you can do that too).

## What are ACKs?

In order to fully understand what's going on, we need to understand a bit of networking here. Not a lot, just enough for this whole process to make sense. the aircrack suite of tools works based off a TCP protocol. This requires a 3-way handshake this is a term that refrences how the protocol communicates with itself. This is also how we grab the packet. The 3 parts of the handshake are: `SYN, SYN-ACK, & ACK`.

Syn is a packet sent by a user, the syn then hits a router that sends a Syn-Ack back to the user, then the user sends an ACK back. The whole point is we are capturing these ACK packets in order to give us the encrypted data that holds the password

## Next Steps:

You don't need to do this, but I find it good practice to use at least 2 different wifi connections to make it harder to find your IP address while browsing & creating your email/bank accounts. I would also keep a note as to what wifi connection is used for what. I am personally running 4 connections for different things. This number may grow in the future, but for now it is realitively static. 

You also want to create an email & bank account at this point. This will trigger the tutorial mission to execute within your `Mail.exe` program you can access from the desktop. The attack process is exactly the same, but the IP and target info is different. It goes in this order: 
```
- Read email
- Use whois on the IP
- Phish the Admin
- Gain access
- download password files
- crack them
```
If you can do this, you can do most of the puzzles in the game. The rest of the things I will teach after this are scripts, and how the NPC missions work.

