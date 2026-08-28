_in 1991 **Linus Torvalds** started developing Linux kernel._

# **Command Line**

## **The Shell**
```sh
username@hostname:current_directory
pete@icebox:/home/pete $
```

```$``` ----> normal user

```sh
$ echo Hello world ------> Hello world
```



## **pwd** _(Print Working Directory)_
```$ pwd```  ------> show where you are(note the path stems *from the root directory*.)



## **cd** _(Change Directory)_
```sh
$ cd /home/pete/Pictures   -------> change directory to picture
$ cd Hawaii   -----> change directory from picture to Hawaii
```
```.``` _(current directory). This is the directory you are currently in._

```..``` _(parent directory). Takes you to the directory above your current._

```~``` _(home directory). This directory defaults to your “home directory”. Such as /home/pete._

```-``` _(previous directory). This will take you to the previous directory you were just at._
```sh
$ cd .
$ cd ..
$ cd ~
$ cd -
```



## **ls** (List Directories)
```sh
$ ls
$ ls /home/pete
```
_Filenames that start with ```.``` are hidden can view them with:_
```sh
$ ls -a      ------> a for all
```

```sh
$ ls -l     ------> show detail information(file permissions, number of links, owner name, owner group, file size, timestamp of last modification, and file/directory name.)
```
```sh
pete@icebox:~$ ls -l
total 80
drwxr-x--- 7 pete penguingroup   4096 Nov 20 16:37 Desktop
drwxr-x--- 2 pete penguingroup   4096 Oct 19 10:46  Documents
drwxr-x--- 4 pete penguingroup   4096 Nov 20 09:30 Downloads
drwxr-x--- 2 pete penguingroup   4096 Oct  7 13:13   Music
drwxr-x--- 2 pete penguingroup   4096 Sep 21 14:02 Pictures
drwxr-x--- 2 pete penguingroup   4096 Jul 27 12:41   Public
drwxr-x--- 2 pete penguingroup   4096 Jul 27 12:41   Templates
drwxr-x--- 2 pete penguingroup   4096 Jul 27 12:41   Videos
```

_Can combine flags (```-a``` or ```-l```) together:_
```sh
$ ls -la
```

>```ls -R```      _recursively(بازگشتی) list directory contents_   
>```ls -r```      _reverse order while sorting_
>```ls -t```      _sort by modification time, newest first_



## **touch**

```touch``` _create new empty files_

```sh
$ touch mysuperduperfile
```
```touch```_also used to change timestamps on existing files and directories_
```sh
Exercises
Create a new file
Note the timestamp
Touch the file and check the timestamp once again
```



## **file**
```file``` _show file type_
```sh
$ file banana.jpg
```



## **cat**
```cat```   _see the contents of a file_
```sh
$ cat dogfile birdfile
```
_not great for viewing large files and only meant for short content._



## **less**
 ```less``` _for viewing text files larger_
 ```sh
 $ less /home/pete/Documents/text1
 ```

 _Use the following command to navigate through less:_
* ```q```  Used to quit out of less and go back to your shell.
* ```Page up, Page down``` Up and Down - Navigate using the arrow keys and page keys.
* ```g```  Moves to beginning of the text file.
* ```G```  Moves to the end of the text file.
* ```/search```  You can search for specific text inside the text document. Prefacing the words you want to search with /
* ```h```  If you need a little help about how to use less while you’re in less, use help.



## **history**
to find and run a command you used previously without typing it again.
```sh
$ history
```

```Up Arrow Key``` Viewing commands backwards(one by one)
```Down Arrow Key``` Viewing commands forward(one by one)

```!!``` View the last command executed and execute it

```Ctrl-R``` Reverse Search - for search command

```sh
$ clear     to clear terminal
```
```Tab key```  it will autocomplete command



## **cp** (Copy)
copies of files
```sh
$ cp name of file /directory/of/where/want/copy/file/to
$ cp mycoolfile /home/pete/Documents/cooldocs
```

use **wildcards** to copy multiple files in same time:
* ```*``` used to represent all single characters or any string.
* ```?``` used to represent one character
* ```[]``` used to represent any character within the brackets
```sh
$ cp *.jpg /home/pete/Pictures  ---> copy all .jpg files in current directory
```


* ```-r``` flag used for recursively copy the files and directories within a directory.(use for Copy everything in a folder/directory )
```sh
$ cp -r Pumpkin/ /home/pete/Documents   ---> copy folder pumpkin in that directory
```

* Note: If there are files with the same name in the directory we want to copy use:
```-i``` flag(interactive) use to prompt you before overwriting a file.
```sh
$ cp -i mycoolfile /home/pete/Pictures
```


## **mv** (Move)
use for move and remaining files
similar command ```cp``` in terms of flags and functionality
```sh
$ mv oldfile newfile                    _rename files_
$ mv file2 /home/pete/Documents         _move to different directory_
$ mv file_1 file_2 /somedirectory       _move more than one file_
$ mv directory1 directory2              _rename directory_
```

_like ```cp``` for prompt you before overwriting:_
```sh
mv -i directory1 directory2
```
_Backup from file before overwrite and it will just rename the old version with a ```~```_
```sh
$ mv -b directory1 directory2
```


## **mkdir** (Make Directory)
```sh
$ mkdir books paintings          make multiple directories at the same time
```

_create subdirectories at the same time with the ```-p``` (parent flag)._
```sh
$ mkdir -p books/hemmingway/favorites
```



## **rm** (Remove)
_used to delete files._
_when using ```rm``` Files are lost forever._
```sh
$ rm file1
```
_Write-protected files will prompt you for confirmation before deleting them._
_write-protected directory will not be easily removed._
*```-f``` remove files whitout without prompting the user(no care for force or protectet files)
```sh
$ rm -f file1
```

```-i```  will give you a prompt on whether you want to actually remove the files or directories.
```sh
$ rm -i file
```

*for delete directory :
```sh
$ rm -r directory               _-r is recursive
```
* **Warning:** This deletion is permanent and will not go to the trash.
_To get confirmation for each deletion:_
```sh
rm -ri myfolder
```

```rmdir``` Deletes only empty folders.
```sh
$ rmdir directory
```



## find
to find a file
```sh
$ find /home -name puppies.jpg              write directory  that we want to search file in it, and name of file
```

```sh
$ find /home -type d -name MyFolder             can to find file by type, d = directory
```

* _find do not just search in that directory, it search any subdirectory and file on it._



## help

help you how to use a command or check what flags are available for a command
```sh
$ help echo                         description and the options can use when want to run echo.
```

```sh
$ echo --help                       
```



## man
can see the manuals for a command

```sh
$ man ls
```



## whatis
A brief description of command line programs.
```sh
$ whatis cat
```



## alias
To create an alias for a command
```sh
$ alias foobar='ls -la'             foobar execute ls -la
```
_this command won't save your alias after reboot_

* for permanently **alias** need to add the alias to a configuration file that the shell loads every time
```sh
~/.bashrc       for permanent alias, add alias to this file
```
   * 1. Open the file: _nano ~/.bashrc_
   * 2. Add alias: Go to the end of the file and add a new line with your alias.  _alias foobar='ls -la'_
   * 3. Save and exit: Press ```Ctrl+X```, then ```Y```, then ```Enter```
   * 4. Reload your shell: To apply the change without restarting your terminal  _source ~/.bashrc_

```sh
$ unalias foobar            remove aliases
```



## exit
 To exit from the shell
 ```sh
 $ exit
```
Or the logout command:
```sh
$ logout
```



***END Command Line***