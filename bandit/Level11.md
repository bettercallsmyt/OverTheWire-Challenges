
# Bandit 10 - 11

[Challenge](https://overthewire.org/wargames/bandit/bandit11.html)

---

## What I Had to Do
Password is stored in ``data.txt`` which is **base64** encoded, so need to decode and then view the password.

---

## How I Did It

So for this we use `base64` command in which man page it says that it encode/decode the file data:
```bash
base64 -d data.txt
```
We use `-d` option which means decode the data of the file.

Now you have the password for the next challenge and log in to the bandit11, so enter this command:
```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```
Now enter the password and you have successfully completed this challenge.

Learn and Enjoy!

---

## What I Learned
- `base64` - method of encoding and decoding data and use of this command

---

## Password
`[REDACTED]`
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

---

## Helpful Reading Material
- `man base64` - to learn more options of bse64 command
- [base64](https://www.freecodecamp.org/news/what-is-base64-encoding/) - to learn about base64 encoding(i just understand that it's a way of encoding data into another form which is not easily understandable)