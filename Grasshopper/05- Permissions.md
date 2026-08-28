# **Permissions**

## **File Permissions**
```sh
$ ls -l Desktop/
drwxr-xr-x 2 pete penguins 4096 Dec 1 11:45 .
```
There are four parts to a file's permissions:
```d``` is for directory, show for the file type
The permissions are grouped into 3 bits each:
                             The first 3 bits are user permissions, 
                             then group permissions, and 
                             then other permissions.


```sh
d | rwx | r-x | r-x
```
```r```: readable
```w```: writable
```x```: executable (basically an executable program)
```-```: empty


## **Modifying Permissions**
```chmod``` command is for Changing permissions:
* First, pick which permission set you want to change: user, group, or other.
* You can add or remove permissions with a ```+``` or ```-```.
```sh
Example: Adding permission bit on a file
chmod u+x myfile
```
above command:
             change permission on ```myfile``` by adding the executable permission(```x```) bit to the user set.

```sh
Example: Removing permission bit on a file
chmod u-x myfile
```

```sh
Example: Adding multiple permission bits on a file
chmod ug+w
```

_another way to **change permissions** using numerical format_

The numerical representations are seen below:
                                            4: read permission
                                            2: write permission
                                            1: execute permission
```sh
chmod 755 myfile            (7) represents user permissions,
                            (5) represents group permissions, 
                            last 5 represents other permissions.
```
**Notice**:
            ```7``` = 4 + 2 + 1, so 7 is the **user permissions**, and it has **read**, **write**, and **execute permissions**.

            ```5``` = 4 + 1, the group has **read** and **execute permissions**.

            ```5``` = 4 + 1, and all other users have **read** and **execute permissions**.



## **Ownership Permissions**
can also modify the group and user ownership of the file.

**Modify user ownership**
```sh
sudo chown patty myfile         -->     set the owner of **myfile** to **patty**.
```


**Modify group ownership**
```sh
sudo chgrp whales myfile        -->      set the group of **myfile** to **whales**.
```


**Modify both user and group ownership at the same time**
can set both the user and group at the same time, if add a colon(```:```) and **group name** after the **user**.
```sh
sudo chown patty:whales myfile
```



## **Umask**
Every file that created comes with a default set of permissions.
To change that default set of permissions, use ```umask``` command.
```umask```This command uses the 3-bit permission set.
```sh
umask 021
```
Instead of adding these permissions, however, ```umask``` takes away these permissions.

                    ## **this section(umask) need to develope**##
                    ## **this section(umask) need to develope**##
                    ## **this section(umask) need to develope**##



## **Setuid**
**The Set User ID** (```SUID```) allows a user to run a program as the owner of the program file rather than as themselves.
- Example: want to change my password, use the ```passwd``` command:
-- It's modifying a couple of files, but most importantly it's modifying the ```/etc/shadow```. this file is owned by root
```sh
passwd

$ ls -l /etc/shadow             --->       -rw-r----- 1 root shadow 1134 Dec 1 11:45 /etc/shadow

$ ls -l /usr/bin/passwd         --->       -rwsr-xr-x 1 root root 47032 Dec 1 11:45 /usr/bin/passwd
```
> Above permission bit here **s**:  is the **SUID**

**Modifying SUID**
are two ways to modify SUID permissions:

1. _Symbolic way:_
```sh
sudo chmod u+s myfile
```
2. _Numerical way:_
```sh
sudo chmod 4755 myfile                  --> the SUID is denoted by a 4
```



## **Setgid**
> Is a **set group ID** (```SGID```) permission bit. 
> This bit allows a program to run as if it were a member of that group.
Example:
```sh
$ ls -l /usr/bin/wall           -->         -rwxr-sr-x 1 root tty 19024 Dec 14 11:45 /usr/bin/wall
```

**Modifying SGID**
```sh
sudo chmod g+s myfile
sudo chmod 2555 myfile              -->     The numerical representation for SGID is 2.
```



## **Process Permissions**
> Processes in Linux have three user IDs (UIDs):
1. ```effective user ID```
This UID determines the process's access level to system resources. Typically, this is the same as the actual UID, unless the SUID bit is set.

2. ```Real User ID```
This is the ID of the user that launched the process. These are used to track down who the user who launched the process is.

3. ```saved user ID```
This allows a process to switch between the effective UID and real UID, and vice versa. 

When you run a command like ‍‍‍```passwd``` that has the **SUID** bit set, your **effective UID** is temporarily changed to _zero_ (the UID of the root user).
Because your **real UID*** remains fixed, the program knows that you are not the root user and cannot change other users' passwords.



## **The Sticky Bit**
**sticks a file/directory** meaning that only the owner or the root user can _delete_ or _modify_ the file. This is very useful for shared directories.
‍‍‍
```sh
$ ls -ld /tmp          -->     drwxrwxrwx+t 6 root root 4096 Dec 15 11:45 /tmp
```
> ```t``` is means everyone can _add__ files, _write_ files, and _modify_ files in the ```/tmp directory```, but only root can delete the ```/tmp``` directory.

**Modify sticky bit**
```sh
sudo chmod +t mydir

sudo chmod 1755 mydir           -->  The numerical representation for the sticky bit is 1.
```

## **End Permissions** ##