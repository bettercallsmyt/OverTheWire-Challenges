
# Bandit 14 - 15

[Challenge](https://overthewire.org/wargames/bandit/bandit15.html)

---

## What I Had to Do
I have to submit the password of current level `bandit14` on the same machine running a TCP service on **port 30000** on **localhost** 

---

## How I Did It

So first i learn about `telnet` and `nc` command.

Then i use `telnet` command to connect to the localhost (the machine itself `bandit14`) on port 30000 by running this simple command:
```bash
telnet localhost 30000
```
Then you just need to enter the password of this current level in to the terminal and it returns you with the password for the next level and this is how you solve this challenge.

You can also run ``nc`` short for `netcat` command to connect to the localhost:
```bash 
nc localhost 30000
```
And then same just enter the password and it will give you the password for the next level.

Just run this command to login to `bandit15` :
```bash 
ssh bandit15@bandit.labs.overthewire.org -p 2220
```
Then enter the password you just found and you have successfully completed this challenge.

Learn and Enjoy!

---

## What I Learned
- ``telnet`` - tool use to connect to remote server and communicate through TCP/IP network.
- ``nc`` - short for netcat tool which also works same as telnet but much powerful than that.

---

## Password
`[REDACTED]`

---

## Helpful Reading Material
- ``man telnet`` - to connect to running service on a server
- `man nc` - same as telnet but much powerful
- [telnet](https://www.geeksforgeeks.org/linux-unix/telnet-command-in-linux/) - to learn more about telnet tool
- [nc](https://www.geeksforgeeks.org/linux-unix/practical-uses-of-ncnetcat-command-in-linux/) - to learn more about netcat tool
