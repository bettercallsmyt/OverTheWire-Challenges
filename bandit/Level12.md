
# Bandit 11 - 12

[Challenge](https://overthewire.org/wargames/bandit/bandit12.html)

---

## What I Had to Do
Password is stored in `data.txt` but all the alphabets lowercase(a-z) and uppercase(A-Z) have been rotated by 13 positions (ROT13 translation).

---

## How I Did It

So first i use ls to find `data.txt` in current working home directory and then learn about `tr` command which can be used to translate or delete characters from the file text or string and use this command to rotate the position of characters by 13 value:
```bash
cat data.txt | tr a-zA-Z n-za-mN-ZA-M
```

This command translate both lowercase and uppercase alphabets to their 13th positions, for example a becomes n and vice-versa and applies for all the alphabets.

We can also use square brackets for *arrays of tr command* [ ], means we can put \[a-z] \[A-Z]  \[n-z]\[a-m]\[N-Z]\[A-M] and other ways too.

Now you have the password just enter the command to log in to bandit12:
```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
```

Now you have successfully completed this challenge.

Learn and enjoy!

---

## What I Learned
- `ROT13 translation` - in this, characters rotated their positions by 13 place.
- ``tr command`` - use to translate characters

---

## Password
`[REDACTED]`


---

## Helpful Reading Material
- ``man tr`` - to learn about tr command such as options, arrays and how to use it
- [ROT13](https://medium.com/@piyush.kochhar1/rot13-a-missing-guide-c811427cfe6e) - To understand ROT13 and how to use tr command to translate characters from it
