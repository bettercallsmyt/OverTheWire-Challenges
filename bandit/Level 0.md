
# Bandit 01

[Challenge](https://overthewire.org/wargames/bandit/bandit0.html)

---

## What I Had to Do

In Level 0, I have to login first into the challenge using **SSH** (Secure Shell).

---

## How I Did It

I am learning Linux from **Linux Basics for Hackers by OTW** book, but in that in starting phase there's no introduction to SSH so first i need to learn about SSH from YouTube.

### SSH 


**Basic commands:** 
```Bash
ssh user@hostname
ssh key-gen  #to generate a pair of authentication keys(Public and Private Key)
ssh-copy-id user@hostname  #to send the public key to server for authentication process

ssh user@hostname -p 22  #To connect to the default port for SSH which is Port 22

```

**Some More commands I learned:**
```Bash
man scp  #scp command is used to how you gonna copy the files over the connection.

sudo systemctl start ssh #to run a ssh server on your own computer in your local network.
systemctl status ssh     #to check the status of running ssh server (it also tells ssh running on which port)

sudo nano /etc/ssh/ssh_config
#to configure the ssh daemon that's running your ssh server.(You can change anything like default port(Port forwarding another topic),default password or authentication via keys, which users to connect only)

```

Credentials to log in to the game: 

**Username**: bandit0

**Host:** bandit.labs.overthewire.org

**Password**: bandit0

**Port:** 2220

To login i need to enter this command:
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Then it will gonna ask you for the Password, Just enter the password displayed on Level 0 instructions and you are then entered into the game.

Learn and Enjoy!

---

## What I Learned
- ``ssh`` - Secure Shell, How to login to the server running SSH.
- ``Public and Private Key Generation`` - Private Key only for client and Public key to connect to servers.
- ``Port Forwarding`` - Need to learn to know how SSH server works and how to make them secure when running on internet.

---

## Password
`[REDACTED]`

---

## Helpful Reading Material
- [SSH Tutorial](https://youtu.be/WwGRGfLy6q8?si=_YuLUaDWFdmp3CKQ) - To learn about SSH basics
- [Linux Basic For Hackers](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://kea.nu/files/textbooks/humblesec/linuxbasicsforhackers.pdf&ved=2ahUKEwj91vDf86GUAxU0e2wGHXuuJtcQFnoECBEQAQ&usg=AOvVaw377-oYwYrP25nObGPAFMpv) by OccupyTheWeb
