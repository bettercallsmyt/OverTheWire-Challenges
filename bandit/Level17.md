
# Bandit 16 - 17

[Challenge](https://overthewire.org/wargames/bandit/bandit17.html)

---

## What I Had to Do
So first i need to find which ports having servers listening on them and then find that 1 port from them which speak SSL/TLS and that port give me the *Private RSA Key* to login to `bandit17` and from there like previous level `/etc/bandit_pass/bandit17` i found the password for the next level to login to.

---

## How I Did It

So as per level i first scan for all the ports between the range of **31000 to 32000** running servers listening on them via two following methods i learnt:
- `nc` - use for port scan (can read on it's man page)
- `nmap` - tool for scanning networks

So first let's use `nc`  short for `netcat` to scan for open ports which allows connection:
```bash
nc -z -v localhost 31000-32000 2>&1 | grep succeeded
```
So `-z ` option is used to tell the `nc` command to scan the ports and `-v` option means *verbose* means tells what happens then localhost (means the machine itself) and the port range of 31000-32000 and `2>&1` to discard the error messages and we use `grep` command to filter the results and show only the succeeded connection, so now it gives 5 open ports but we don't know which one speaks SSL/TLS protocol.

So we can check that too one by one:
```bash
openssl s_client -connect localhost:portnumber -quiet
```
If it replies with the *Private RSA key* after entering the password means it's the one which speaks SSL/TLS protocol.

Now we can also use `nmap` command to find the open port and also the method it uses to speak in one line command:
```bash
nmap -sV -T4 localhost -p 31000-32000 
```
In this command we use`nmap` for the scanning of port and `-sV` option so the command tells the version of service such as `ssl` in our case and `-T4` to fasten the scan and localhost to tell the `nmap` to scan on the same machine and `-p` to specify the port range, and it also gives you the open port and also the service they are using and from our search we find that `port 31790` is the port that we need which is running `ssl/unknown` as the service.

So now we connect to that port using `openssl s_client` command as we did in previous level:
```bash
openssl s_client -connect localhost:31790 -quiet
```
We use `s_client` which is a tool to connect to a host using SSL/TLS and `-connect` option to tell to connect to the localhost on  31790 port and `-quiet` option is must it just stops printing of certs information and other things and make things clearer.

**Note** - I don't get the *Private RSA Key* without that `-quiet` option maybe the key goes somewhere else or it's just an error so use this option.

And after you enter the password of current level you get a *Private RSA Key*, which you can try to use to login to `bandit17` from the current shell of `bnadit16` but unable to do so as it was in the level [[Level 14]] , but still i write those commands here to login to `bandit17` directly from `bandit16`:
```bash
mktemp -d # to create a directory in temp you can also use mkdir in /tmp to make a directory
cd /tmp/tmp.GnFsRBZBf0 # to navigate to that directory
nano rsaprivate.key #to create a file in which you gonna paste your key
chmod 400 rsaprivate.key
ssh -i rsaprivate.key bandit17@bandit.labs.overthewire.org -p 2220 #type yes for fingerprint
```

But it doesn't gets you connected as i think bandit stopped connecting from one level to another or as localhost to save sources you can check their website for more info so we need to copy the private key to our local machine and from there use `ssh` command to connect to `bandit17` the process is same just do it on your local machine:

And when you entered in the `bandit17` you can find the password in the:
```bash
cat /etc/bandit_pass/bandit17
```

And now you have the password for the `bandit17` just run this command:
```bash
ssh bandit17@bandit.labs.overthewire.org -p 2220
```

Learn and Enjoy!

---

## What I Learned
- `Port Scanning` - how to scan ports using `nc` and `nmap` for a range of ports
- `Port Service` - to know what service port is using such as TCP, UDP, SSL and so on
- `Port Connection` - how to connect to port which speaks SSL/TLS protocol
- `Login to server using RSA key` - login using RSA private key authentication 
---

## Password
`[REDACTED]`

---

## Helpful Reading Material
- `man nmap` - to know more about options of nmap scanner
- `man nc` - go to section of port scanning to learn how it can be use to scan for open ports
- `man openssl s_client` - to know how it can be used to connect to ports which speaks SSL/TLS protocols
- `man ssh` - how you can use identity file to authenticate via private RSA key
- [Check Open Ports](https://linuxize.com/post/check-open-ports-linux/) - to learn how you can check for open ports
- [Identify SSl/TLS protocol is enabled/disabled on port](https://knowledge.informatica.com/s/article/How-to-identify-if-a-SSL-TLS-protocol-is-enabled-disabled-on-a-particular-port?language=en_US) 
- [Nmap Scanning Technique](https://www.geeksforgeeks.org/ethical-hacking/port-scanning-techniques-by-using-nmap/)
