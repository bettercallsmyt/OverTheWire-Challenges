
# Bandit 12 - 13

[Challenge](https://overthewire.org/wargames/bandit/bandit13.html)

---

## What I Had to Do
To find a password stored in `data.txt` which is a hexdump (hexadecimal) of a file with multiple compression, needed to decompress the file again and again in order to find the password.

---

## How I Did It
This is one of the hardest challenge till yet that i have encountered so for this first i list all the commands that i use:
- **ls** - to list the files and directories
- **mkdir** - to create a new directory
- **cp** - to copy a file
- **cd** - to change working directory
- **xxd** - to convert hexadecimal file back to binary file
- **cat** - to view the content of the file
- **gzip** - to compress/decompress the file with .gz, .z
- **file** - to know what type of file it is
- **mv** - to rename or move a file
- **bzip2** - to compress/decompress the file which is bzip2 compressed
- **tar** - to create an archive or extracting files from an archive

So this are the command that we need to use and i take help from internet too for this challenge, cause i can't think how to start solving this after making directory and copying file, so let's start this.

First i make a new directory in ``/tmp`` directory named *smyt* using `mkdir` command:
```bash
mkdir /tmp/smyt
```

Then i copy the file `data.txt` from the home directory to the new directory i've just created:
```bash
cp data.txt /tmp/smyt
```

Now we need to navigate to our new directory for this we use ``cd`` command:
```bash
cd /tmp/smyt
```

Now we can see that our file is copied here using ``ls`` command.

So now first we need to convert this hexadecimal file back to the binary file, for this we use `xxd` command with `-r` option which stands for reverse:
```bash
xxd -r data.txt > data
```
This command converts the hexadecimal file to binary in our directory with the name of data because we use output redirector (>) and now you confirm this by using ``ls`` comand.

Now we have our binary file, but we still don't have the password cause the file is compressed repeatedly so now we check what type of file is `data` file using ``file`` command:
```bash
file data
data: gzip compressed data, was "data2.bin", last modified: Fri Apr  3 15:17:36 2026, max compression, from Unix, original size modulo 2^32 576

```
The output shows that the file is gzip compressed so we need to unzip it for this we use ``gzip`` command with `-d` option or directly `gunzip` command which is used to decompress the gzip compressed file.

But before that we need to change the extension of our file `data` so the gzip command can work so we gonna use ``mv`` command to rename our file:
```bash 
mv data data.gz
```

Now we can decompress this using this command:
```bash
gunzip data.gz
```
Now you can check with `ls` command that the file is now decompressed and convert into new file *data* , so now first we check what type of file we got via:
```bash
file data
data: bzip2 compressed data, block size = 900k
```
It shows that file is now bzip2 compressed, so now we need to follow the same procedure but with ``bzip2`` command with `-d` option or `bunzip2` command, but before that we need to rename the file:
```bash 
mv data data.bz
```
Because `bzip2` only work on this type of file, now decompress the file using this command:
```bash
bzip2 -d data.bz
```
Now it decompress the file and makes it *data* file again which you can check with `file command` and you find out that this is now `gzip`  compressed, so we need to use this command:
```bash
mv data data.gz
gunzip data.gz
```
Now again we have data file but this time it's a tar archive means we need to use `tar` command to open this archive file with `-xvf` option:
```bash
tar -xvf data
```
In this command we use three options in which `-x` means extract the file from the archive, `-v` means verbose show all the progress and `-f` to specify the file name of the archive which is *data* in our case and it gives you output on screen of **data5.bin** and if you run `ls` command you can see `data5.bin` is in the directory so now let's work on `data5.bin`:
```bash
file data5.bin  #it's a tar archive
tar -xvf data5.bin
```

Now it shows output on screen `data6.bin` and you can see this file is in the directory using `ls` command, so now let's work on `data6.bin` file:
```bash
file data6.bin  # it's bzip2 compressed file
mv data6.bin data6.bz
bzip2 -d data6.bz  # to decompress the bzip2 compressed file
```

This give us the file `data6` in the directory, you can confirm via `ls` command, now let's work on `data6` file:

```bash
file data6  #it's also a tar archive
tar -xvf data6 
```
It gives output on screen `data8.bin` file, so now let's work on `data8.bin` file:
```bash
file data8.bin  # it's gzip compressed data file
mv data8.bin data8.gz
gunzip data8.gz
```

This gives us the file `data8` in our directory, now let's see what type of file is `data8`:
```bash
file data8  #it's an ASCII text file
cat data8
```
And now you have finally find the password to login to bandit13, so now run this command:
```bash 
ssh bandit13@bandit.labs.overthewire.org -p 2220
```

Now just enter the password and you have successfully completed this challenge.

Learn and Enjoy!

---

## What I Learned
- `Hexadecimal file` - what is a hexdump of a file
- ``creating a new directory`` - using mkdir command
- ``copying a file`` - how to copy a file from one place to another using cp
- ``conversion of hexadecimal to binary file`` - how to convert hexadecimal file into binary using `xxd`
- `Compression and Decompression of file` - how to compress and decompress file using various methods such gzip, bzip2.
- `Making an archive and extracting it` - how to make an archive and how to extract it using tar command

---

## Password
`[REDACTED]`

---

## Helpful Reading Material
- `man mkdir` - to learn about how to make directories
- `man cp` - to know more about copying a file
- `man xxd` - to convert hexadecimal file into binary and vice-versa
- `man gzip` - to compress and decompress file with .gz like extensions
- `man bzip2` - same as gzip but for .bz .z files
- `man mv` - to rename a file or to move a file
- `man tar` - to make an archive of files or to extract them from archive
- [xxd](https://www.geeksforgeeks.org/linux-unix/xxd-command-in-linux/) - to learn more about xxd command and how you can use it
- [tar](https://www.geeksforgeeks.org/linux-unix/tar-command-linux-examples/) - to learn more about tar command and it's options and how to use them to make an archive or to extract an archive.
