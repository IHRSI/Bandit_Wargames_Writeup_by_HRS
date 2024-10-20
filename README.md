# Bandit_Wargame_OverTheWire_Writeup
Writeups for bandit wargames levels
## Level 0
### Commands used
`ssh bandit0@bandit.labs.overthewire.org -p 2220 `
### Flag
> bandit0
### Resources used
[SSH wikipedia](https://en.wikipedia.org/wiki/Secure_Shell) to know about SSH. 

## Level 0 → Level 1
### Commands used
```
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls -a
cat readme
exit
```
* Note that exit will be used in every level.
### Flag
>ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
### Approach used
I connected to the ssh using the password we got from last level then used 'ls -a' to list all the files. After that I used the command ' cat readme' to read the contents of the file 'readme' and there I got the password for level 2.

* Note that password of the last level will be used to connect to the ssh everytime.

## Level 1 → Level 2
### Commands used
```
ssh bandit1@bandit.labs.overthewire.org -p 2220
ls -a
cat ./-
```

### Flag
>263JGJPfgU6LtdEvgfWU1XP5yac29mFx
### Approach used 
After connecting to the ssh and listing the files I used the command 'cat ./-' to read contents of hyphen file and then we got the password for the next level.

# Level 2 → Level 3
### Commands used
```
ssh bandit2@bandit.labs.overthewire.org -p 2220
ls -a
cat spaces\ in\ this\ filename
            or
cat "spaces in this filename"
```
### Flag 
>MNk8KNH3Usiio41PRUEoDFPqfxLPlSm
### Approach used
After connecting to the ssh and listing the files I used the command 'cat spaces\ in\ this\ filename ' to read contents of the file and there we got the next password. Alternative command can be cat "spaces in this filename" also.

# Level 3 → Level 4
### Commands used 
```
ssh bandit3@bandit.labs.overthewire.org -p 2220
ls -a
cd inhere/
ls -a
cat ...Hiding-From-You
```

### Flag
>2WmrDFRmJIq3IPxneAaMchapopFhF3NJ
### Approach used
After connecting to ssh, we have to go inside a directory named 'inhere/'. Now type the next command 'ls -a' which will give us all files in a list. Inside the directory you will see a file named '...Hiding-From-You' and we have to read this to get the next password.

# Level 4 → Level 5
### Commands used
```
ssh bandit4@bandit.labs.overthewire.org -p 2220
ls 
cd inhere/
ls
file ./-file00
.
.
.
.
file ./-file09
cat ./-file07
```
 **OR**
 ```
ssh bandit4@bandit.labs.overthewire.org -p 2220
ls 
cd inhere/
ls
file ./*
cat ./-file07
```
### Flag 
>40QYVPkXZO0E005pTW81FB8j8lxXGUQW
### Approach used 
After connecting to the ssh I entered the 'inhere' directory then listed all the files. In the first method I have to check file type for every file by using ' file ./-fileXX' again and again which is very time consuming to do instead of doing that I used the second method through which I can see the file type of every file in the directory by just using one command ' file ./*'. Then I just used 'cat' command to read the 'ASCII text' file that is the file '-file07' to get the password.
### Resources used
[phoenixNAP](https://phoenixnap.com/kb/linux-file-command)

# Level 5 → Level 6
### Commands used
```
ssh bandit5@bandit.labs.overthewire.org -p 2220
ls 
cd inhere/
ls
find . -size 1033c -readable ! - executable
cat ./maybehere07/.file2
```
**or**

`find . -size 1033c -type f ! - executable`

### Flag
>Hwasnphtq9AVKe0dmk45nxy20cvUa6EG
### Approach used
After entering the 'inhere' directory we will 20 more directories named from 'maybehere00' to 'maybehere19'. Now I used the find command to find a file which is human readable, not executable(used '!' for not) with keeping the size 1033c (here c means bytes) as given in the question, which gave me the output './maybehere07/.file2'. Then I just used the 'cat' command on this file to get the password.To know about file attributes i used man file command in the terminal.Alternative for readable is type(of file) with attribute f(it specifies regular file- they are readable).
### Resources used
find command from '[Commands you may need to solve this level](https://man7.org/linux/man-pages/man1/find.1.html)'

#  Level 6 → Level 7
### Commands used 
```
ssh bandit6@bandit.labs.overthewire.org -p 2220
find / -user bandit7 -group bandit6 -size 33c
cat /var/lib/dpkg/info/bandit7.password
```

**or**

```
ssh bandit6@bandit.labs.overthewire.org -p 2220
cd /
find . -user bandit7 -group bandit6 -size 33c
cat /var/lib/dpkg/info/bandit7.password
```

### Flag
>morbNTDKSW6jIlUc0ym0dMaLn0lFVAaj
### Approach used
After connecting to the server we will just use the find command to find a file with user name 'bandit7' and in group 'bandit6' with a size of 33 bytes. We will get a big list of files and we just need to find a location where ' permission denied' is not written. On searching we will find '/var/lib/dpkg/info/bandit7.password' and then we will just use 'cat' command. We use cd / command to go to root directory as the file which has password is somewhere in the sever whose two alternate ways are shown to retrive the password in the commands above.
