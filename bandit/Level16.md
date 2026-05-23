
# Bandit 15 - 16

[Challenge](https://overthewire.org/wargames/bandit/bandit16.html)

---

## What I Had to Do
To find the password for the next challenge i have to submit the password of the current level `bandit15` to the port 30001 on localhost using TLS/SSL encryption. 

---

## How I Did It

First i learn about `openssl` and `s_client` command.

`openssl` - tool used for secure network communication using TLS and SSL protocols and cryptography.

`s_client` - command used with openssl to connect to running services on a server on port using TLS and SSL protocols

So after learning about the syntax of command `s_client` i run this command:
```bash
openssl s_client -connect localhost:30001 
```

This connects to localhost means the machine itself `bandit15` on port `30001` over TLS and SSL protocol or encryption via s_client command.

Now after you submit the password of the current level you will receive the password for the next level and then just run this command:
```bash
ssh bandit16@bandit.labs.overthewire.org -p 2220
```

Now enter the password you received and you have successfully completed this challenge.

Learn and Enjoy!

---

## What I Learned
- TLS is the protocol → OpenSSL is the software implementing it → s_client is a tool within OpenSSL to test/use it. - This is the key learning of this level
- **SSL/TLS** = just a set of rules (protocol) that defines _how_ the encryption handshake happens, how keys are exchanged, how data gets encrypted in transit. It doesn't do anything by itself — it's just the specification.
- **OpenSSL** = the actual software that _implements_ those rules. It's what makes the handshake actually happen, does the crypto math, and lets you interact with services that speak that protocol.

---

## Password
`[REDACTED]`
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

---

## Helpful Reading Material
- `man openssl` - to learn about openssl and how it works
- `man s_client` - how it is used to connect to service running using tls/ssl encryption.
- [openssl command](https://www.baeldung.com/linux/openssl-command-examples) - to learn how openssl command works