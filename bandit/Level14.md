
# Bandit 13 - 14

[Challenge](https://overthewire.org/wargames/bandit/bandit14.html)

---

## What I Had to Do
I have to find the password on `bandit14` which is stored in ``/etc/bandit_pass/bandit14`` but the catch is that `bandit13` have only private key which can be used to login onto `bandit14` which is the next level and then on `bandit14` you found the password for the `bandit14` login.

---

## How I Did It

So first of all i learned about ssh from different sources such as YouTube, Blogs, Ubuntu official page, asking Claude and then able to solve the challenge.

So first i run `ls` command on `bandit13` on which i login to see the content of home directory:
```bash
bandit13@bandit:~$ ls
HINT  sshkey.private
```
It have private ssh key as stated which can be used to login to `bandit14` by this command:

```bash
ssh -i sshkey.private bandit14@localhost -p 2220
```
In this command, `-i` option is used for stating that selects a file from which the private key for public key authentication is used.

And we are connecting as localhost

But unfortunately this command doesn't work the main reason behind this is:
- That you can't login from `bandit` server to another `bandit` server.
- And also can't login to `bandit` server as localhost

So we need to connect to `bandit14` from our local machine, for this we can use two methods: 
- directly copying of ssh private key from Ctrl+C and Ctrl+V with the name exact at it is on our local machine.
- or we can use ``scp`` command for copying the file securely from the server to our local machine

So for approach 2 i am gonna use this command: 
```bash 
scp -P 2220 bandit13@bandit.labs.overthewire.org:~/sshkey.private .
```
Explanation of this command:
- `scp` - used for OpenSSH secure file copy from server to local machine
- `-P` - option for telling which port to use and to connect
- `bandit13@bandit.labs.overthewire.org` - telling the username and domain name on which server to connect to and as what user
- `:` - used as a separator that the first part is user part and other part is file part
- `~` - used for the home directory of `bandit13`
- `./sshkey.private` - the private key file that needs to copy
- `.` - means copy in the current directory

So for this then you need to enter the password of `bandit13` which you've found on the previous challenge and now you have the file, but in order to run the file you need to change it's permission for this we gonna use `chmod` command on our local machine:
```bash
sudo chmod 600 sshkey.private
```
And now the permission is changed and this file is ready for authentication to log in onto `bandit14`

So now run that command once again but this time from the local machine and on the server bandit.labs.overthewire.org instead of localhost:
```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```
And now via key-pair authentication you have successfully login onto `bandit14` now let's see the password which is stored in `/etc/bandit_pass/bandit14`
```bash
cat /etc/bandit_pass/bandit14
```
So now you have the password for the next level and you use it to login onto `bandit14`  via password authentication.
```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220
```

Learn and Enjoy! 


---

## What I Learned
- ``SSH`` - How ssh works and it's key pair authentication
- `scp` - how to copy files securely from server to the local machine 
- `Permission Modification` - How to change permissions of file
- `How to login to server using private key via -i option for identity file`

---

## Password
`[REDACTED]`

---

## Helpful Reading Material
- `man ssh` - to learn more about ssh protocol and it's options
- `man scp` - to learn more about how to copy files via ssh
- `man chmod` - to know how to change permissions of file
- [ssh](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) - to learn about ssh key pair and authentication of it
- 
