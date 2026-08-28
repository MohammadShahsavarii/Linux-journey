# **User Management**

## **Users and Groups**

```sudo``` command(superuser do) is used to run a command with root access.
```sh
$ cat /etc/shadow           -->   get a permission denied error for to view a protected file
```
```sh
$ ls -la /etc/shadow


-rw-r----- 1 root shadow 1134 Dec 1 11:45 /etc/shadow
```

```sh
$ sudo cat /etc/shadow          -->     be able to see the contents of the file
```



## **Root**

```Question``` how do you know who has access to do ```sudo```? 
                There is a file called the ```/etc/sudoers``` file, this file lists users who can run ```sudo```.
                Also can edit this file with the ```visudo``` command.



## **/etc/passwd**
```/etc/passwd``` to find out what users are mapped to what ID
```sh
$ cat /etc/passwd
```
            ```sh
            output:(ex:first line)
                    root:x:0:0:root:/root:/bin/bash
            ```
                    1. Username
                    2. User's password:
                                      if see an ```"x"``` that means the password is stored in the ```/etc/shadow``` file,
                                      a ```"*"``` means the user doesn't have login access,
                                      if there is a ```blank```( ) field that means the user doesn't have a password.
                    3. The user ID - as you can see root has the UID of 0
                    4. The group ID
                    5. GECOS field - This is used to generally leave comments about the user or account such as their real name or phone number, it is comma delimited.
                    6. User's home directory
                    7. User's shell - you'll probably see a lot of user's defaulting to bash for their shell



## **/etc/shadow**
The ```/etc/shadow``` file is used to store information about user authentication.It requires ```superuser(sudo)``` read permissions.
```sh
$ sudo cat /etc/shadow


root:MyEPTEa$6Nonsense:15000:0:99999:7:::
```
it is same to ```/etc/passwd``` but has different.
        1. Username,
        2. Encrypted password,
        3. Date of last password changed - expressed as the number of days since Jan 1, 1970. If there is a 0 means user should change password next time login,
        4. Minimum password age - Days that a user will have to wait before being able to change their password again
        5. Maximum password age - Maximum number of days before a user has to change their password
        6. Password warning period - Number of days before a password is going to expire
        7. Password inactivity period - Number of days after a password has expired to allow login with their password
        8. Account expiration date - date that user will not be able to login
        9. Reserved field for future use



## **/etc/group**
```/etc/group``` file allows for different groups with different permissions.
```sh
$ cat /etc/group


root:*:0:pete
```
                1. Group name
                2. Group password - using an elevated privilege like sudo is standard. A "*" will be put in place as the default value.
                3. Group ID (GID)
                4. List of users - you can manually specify users you want in a specific group



## **User Management Tools**

useful commands to run to manage users:

**Adding Users**
use the ```adduser``` or the ```useradd``` command.
```adduser```contains more helpful features such as making a home directory and more.
```sh
$ sudo useradd bob
```


**Removing Users**
```userdel``` To remove a user:
```sh
$ sudo userdel bob
```


**Changing Passwords**
```sh
$ passwd bob          -->     allow you to change the password of yourself or another user (if you are root).
```


## **End User Management** ##