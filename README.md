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

# Level 7 → Level 8
### Commands used
```
ssh bandit7@bandit.labs.overthewire.org -p 2220
ls
cat data.txt | grep "millionth"
```

**or**
```
ssh bandit7@bandit.labs.overthewire.org -p 2220
ls
grep "millionth" data.txt
```

### Flag
>dfwvzFQi4mU0wfNbF0e9RoWskMLg7eEc
### Approach used
After using 'ls' command we will get only one file named 'data.txt'. Now by using 'cat' and 'grep' command together, we will find the word 'millionth' and the password is written in front of it. We can also accomplish it by using only grep and file name.
### Resources used
learnt about grep from [Grep Command in Linux ](https://www.freecodecamp.org/news/grep-command-in-linux-usage-options-and-syntax-examples/#:~:text=grep%20is%20short%20for%20%22global,a%20powerful%20command%20to%20use.) or use the command 'man grep' to know more about grep in the terminal only.

# Level 8 → Level 9
### Commands used
```
ssh bandit8@bandit.labs.overthewire.org -p 2220
ls
cat data.txt | sort | uniq -c
```
**or**

`sort data.txt | uniq -u`

### Flag
>4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
### Approach used
After listing the files we find the file 'data.txt'. Now we use 'cat' to read the file with using commands like 'sort' to sort the identical texts and 'uniq -c' to to sort all texts lines which are present only once. We will find only 1 text that has appeared once so that is the password.
### Resource used
we can use commands 'man sort' and 'man uniq' to know more about them in the terminal itself.

# Level 9 → Level 10
### Commands used
```
ssh bandit9@bandit.labs.overthewire.org -p 2220
ls
strings data.txt | grep =
```
### Flag
>FGUWS1lLVJrxX9kMYMmlN4MgbpfMiqey
### Approach used
Using the 'cat' command here is not suitable as the file is not a human readable file, so instead we are using the ' strings command to use it to find readable string characters and also using the 'grep' command to find text with '='. We will find texts with equal to in them and one of them is the password.
### Resources used
We can learn about 'strings' command from '[Linux strings command](https://www.javatpoint.com/linux-strings-command)'

# Level 10 → Level 11
### Commands used
```
ssh bandit10@bandit.labs.overthewire.org -p 2220
ls
cat data.txt | base64 -d     or   base64 -d data.txt
```
### Flag
>dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
### Approach used
When we use ' cat data.txt' we can easily see that the file is in base64 because the text is ending with two '='(which tells us that it is base64). So now we use 'cat' with the tool base64 and using '-d' to decode it and get the password.
### Resources used 
using the command 'man base64'.

# Level 11 → Level 12
### Commands used
```
ssh bandit11@bandit.labs.overthewire.org -p 2220
ls
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
### Flag
>7x16WNeHI15YkIhWsfFIqoognUTyj9Q4
### Approach used
After listing the files we will use 'cat' command with tool 'tr' and keeping values ('A-Za-z' 'N-ZA-Mn-za-m') to use rot13 on the text and get our password.
### Resouces used
use 'man tr' to learn about 'tr' tool and [ROT13 Wikipedia](https://en.wikipedia.org/wiki/ROT13) to learn about rot13.

# Level 12 → Level 13
### Commands used
```
ssh bandit12@bandit.labs.overthewire.org -p 2220
ls
cat data.txt   # We can see that it is a hexdump file.
cd /tmp
mkdir hrs
cd hrs
cp ~/data.txt .
cd /tmp/useless1
xxd -r data.txt hex
ls
file hex
mv hex hex.gz
ls
gzip -d hex.gz
ls
file hex
mv hex hex.bz2
bzip2 -d hex.bz2
ls
file hex
mv hex hex.gz
gzip -d hex.gz
ls
file hex
tar -xf hex
ls
file data5.bin
tar -xf data5.bin
ls
file data6.bin
mv data6.bin data6.bz2
bzip2 -d data6.bz2
ls
file data6.bin
tar -xf data6.bin
ls
file data8.bin
mv data8.bin data8.bin.gz
gzip -d data8.bin.gz
ls
file data8
cat data8
```
### Flag
>FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
### Approach used
First I entered the directory 'tmp' then made a file using the 'mkdir' command. Using the copy command 'cp', I copied the file to the 'hrs' directory created by me. then used 'cat' command with the tool 'xxd' to reverse engineer the hexdump file and move it to file named 'hex'. After identifying the file type of 'hex', we will see that it is a gzip file which is very similar to zip file in windows which means we just have to extract it. So we rename 'hex' to 'hex.gz' and then use the gzip tool to decompress the 'hex.gz' file. We will again check the file type of the hex file and see that it is a bzip2 file. So we will again rename the file from 'hex' to 'hex.bz2' and then use the bzip2 tool to decompress the file. Again we will check the file type of the hex file and it is gzip again so same process again after that when we check the file type, this time it is a 'tar'(compressed archive file) file so we will use tar tool with '-xf', where 'x' basically extracts file from archive and 'f' specifies the filename of the archive. We will get a 'data5.bin' file. Again this is a tar file so same step. The we will get 'data6.bin' which a bzip2 file so we will do the same process we did earlier and then again check the file type of the result, which gives us data6.bin file which is in tar format so we will extract it again. This time we will get 'data8.bin' file which is in gzip, so we extract it and get an ASCII file named 'data8'. now, we will just read the file and get the password.
### Resources used
Manual page of gzip, bzip2, tar, mkdir, [Hex dump on Wikipedia](https://en.wikipedia.org/wiki/Hex_dump) and some resources related to extracting files.

# Level 13 → Level 14
### Commands used
```
ssh bandit13@bandit.labs.overthewire.org -p 2220
ls
ssh -i sshkey.private bandit14@localhost -p 2220
cat /etc/bandit_pass/bandit14
```
### Flag
>MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
### Approach used
Using 'ls' we will only find one file named 'sshkey.private' which is basically a private key so we will use the ssh tool with '-i' which basically selects a file from which the identity (private key) for public key authentication is read. Also the user will be bandit14 and host name will be localhost as given in question and as always port should be 2220. After connecting to the neww ssh, just use cat command to read the file given in question i.e. /etc/bandit_pass/bandit14. We will get the password.
### Resources used
Manual page of ssh and some forums on using keys as an alternative for password to connect to ssh.

# Level 14 → Level 15
### Commands used
```
ssh bandit13@bandit.labs.overthewire.org -p 2220
ls
ssh -i sshkey.private bandit14@localhost -p 2220
nc localhost 30000
(put the password from last level only)
```
or
```
ssh bandit14@bandit.labs.overthewire.org -p 2220
telnet localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS(put the password from last level only)
```
### Flag
>8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
### Approach used
While doing Level 13 → Level 14 and after reading the password, we can continue from there only and use 'nc' command to connect to localhost using port 30000 and there we need to paste the password from last level to automatically get the next password. Here nc and telnet command both works similar.
### Resources used
manual page of nc and [The netcat Command in Linux](https://www.tutorialspoint.com/the-netcat-command-in-linux#:~:text=The%20netcat%20command%2C%20also%20known,of%20other%20network%2Drelated%20tasks.)

# Level 15 → Level 16
### Commands used
```
ssh bandit15@bandit.labs.overthewire.org -p 2220
openssl s_client -connect localhost:30001
(Enter the password from last level)
```
### Flag
>kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
### Approach used
As telnet and nc don't use encryption openssl is preffered over it.After connecting to the ssh, we use the openssl tool with 's_client' which basically tells the server we need to connect to. The localhost(server) which is ported to 30001. Then just enter the password from last level to get the password of next level.
### Resources used
manual page of openssl and s_client and the helpful reading material.

# Level 16 → Level 17
### Commands used
```
ssh bandit16@bandit.labs.overthewire.org -p 2220
nmap -sV -T4 -p 31000-32000 localhost
openssl s_client -connect localhost:31518
openssl s_client -connect localhost:31790
cd /tmp
mkdir hrs2
cd hrs2
nano rsafile {do ctrl+S to save the file}
ls
ls -al
chmod 400 rsafile
ssh -i sshkey.private bandit17@localhost -p 2220
cat /etc/bandit_pass/bandit17
```
### Flag
-----BEGIN RSA PRIVATE KEY-----

MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=

-----END RSA PRIVATE KEY-----

### Approach used
First I used the 'nmap' command to scan all the ports in the range 31000 to 32000, then it gave me all the ports that were open. Again I used the 'nmap' tool but this time with '-sV' and '-T4' which basically detects the service/version and to make the scan quicker respectively. Then I used the 'openssl' tool to connect to the two ports which had ssl service and those were 31518 and 31790. After connecting to the 31518 port, I typed the password of level 16 but it just gave me the same password as result so i ended the connection. Then I connected to the 31790 port and typed the level 16 password and this time it told me that it was correct and gave me the private key. Now I just made a rsafile in '/tmp/hrs2' by using the 'nano' command and then saved the key in this file. Then I just used 'ls -al' and found that the rsafile can be read by any user or group so it won't let me connect to bandit17 so I use 'chmod' tool to change the permissions of the file so that only I can access it and then just connect to the bandit17 ssh using rsa key.
### Resources used
manual pages of nmap, nano, chmod. Used [Nano Text Editor in Linux](https://www.geeksforgeeks.org/nano-text-editor-in-linux/) to learn how and when to use a text editor to save the private key I got and used [Change File Permissions (chmod)](https://youtu.be/D3YY1RJKzrA) to learn how and why to change permissions of a file.

# Level 17 → Level 18
### Commands used
```
ssh -i rsafile bandit17@localhost -p 2220
cd /
ls
diff passwords.old passwords.new
```
### Flag
>hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
### Approach used
After connecting to the bandit17 ssh using the private key of last level we will just list the files and see that there are two files 'passwords.old' and 'passwords.new'. As per the question the only line that has been changed between passwords.old and passwords.new is the answer so we will just use the diff tool to see which line is different b/w them and get the password.
### Resources used
manual page of diff.

# Level 18 → Level 19
### Commands used
```
ssh bandit18@bandit.labs.overthewire.org -p 2220 "ls"
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
```
### Flag
>awhqfNnAbc1naukrpqDYcF95h7HoMTrC
### Approach used
I just used the ls command in the same line with ssh tool so by doing this ls will be executed before we logout and after that I repeated the same command and just used 'cat readme' this time to get the password.
### Resources used
I tried to bypass bash by [reading the file through ssh/scp directly](https://stackoverflow.com/questions/27491467/how-to-read-file-through-ssh-scp-directly)
