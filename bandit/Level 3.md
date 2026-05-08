
# Bandit 02 - 03

[Challenge](https://overthewire.org/wargames/bandit/bandit3.html)

---

## What I Had to Do
I have to find the password in the file called --spaces in this file-- to login on to the bandit3 to solve this challenge.

---

## How I Did It

So first i am already logged in into bandit2 using the password i found in - file.

Now i run ls command to see what is inside the current directory(home directory):
```bash
bandit2@bandit:~$ ls 
--spaces in this filename--
```

So when i run cat command to view the content of file it estimates the dashes -- as option --spaces so i have to try the previous level command to view the file with giving it's path:

```bash
bandit2@bandit:~$ cat ./--spaces in this filename--
cat: ./--spaces: No such file or directory
cat: in: No such file or directory
cat: this: No such file or directory
cat: filename--: No such file or directory
```

Then i understood that if there are spaces in the file name then you can use quotes (' ') to write the name of file in commands so command treat the whole name as one:

```bash
bandit2@bandit:~$ cat ./'--spaces in this filename--'
```

Now You have the password to login to the bandit3 just run the command:

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

And then enter the password you found in the file and you've successfully login in to the bandit3.

Learn and Enjoy!

---

## What I Learned
- ``Use of quotes in filename`` -If a file have spaces in it's name always use quotes to treat them as one thing for the command.
- ``file command`` - It just tells you the type of file such as ASCII Text or Binary files etc.

---

## Password
`[REDACTED]`

---

## Helpful Reading Material
- ``man cat`` - to know about it's option usage
- ``man file`` - command to find file type
