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
