# **Text**

## **stdout** (Standard Out)

```stdin``` standard input 
```sh
echo Hello world!           this output's name is stdout
```

```sh
echo Hello world > newfile.txt          write text in file
```
* in command above if file nu exist, will **create** and write on that.
* if file exist, it will **overwrite**

```>``` is _redirection operator_ . It change where standard output goes. 

* if file exist and don't want to overwrite use ```>>```

```sh
$ echo Hello World >> peanuts.txt
```
* if file exist ```>>``` This will append to the end of the exist file, and if file nu exist it will create file like ```>``` 



## **stdin** (Standard In)
_**stdin** from devices like the keyboard, files, output from other processes and the terminal_

```sh
$ cat < peanuts.txt > banana.txt            file has text
```
* _content of peanuts.txt redirect to another file(banana.txt)_



## **stderr** (Standard Error)

_file descriptor for **stdin**, **stdout** and **stderr** is ```0```, ```1```, and ```2``` respectively._

```sh
$ ls /fake/directory > peanuts.txt     --->      ls: cannot access /fake/directory: No such file or directory
```

* want to redirect our ***stderr*** to the file:
```sh
$ ls /fake/directory 2> peanuts.txt
```

* wanted to see both ***stderr*** and ***stdout*** in the ```peanuts.txt``` file:
```sh
$ ls /fake/directory > peanuts.txt 2>&1
```
* shorter way to redirect both stdout and stderr to a file:
```sh
$ ls /fake/directory &> peanuts.txt
```

* want to get rid of stderr messages completely:
_redirect output to a special file call ```/dev/null``` and it will discard any input._
```sh
$ ls /fake/directory 2> /dev/null
```



## **pipe** and **tee**
* ```pipe``` with sign ```|```  allows us to use the output of one command as input to another command.
```sh
$ ls -la /etc
```

```sh
$ ls -la /etc | less        ---> stdout of ls -la /etc and then piped it to the less command. 
```

* ```tee``` Allows you to send the output of a command to two destinations:

    1. The screen (stdout).

    2. One or more files
```sh
$ ls | tee peanuts.txt              ---> write output of command ls into file
```



## **env** (Environment)
```sh
$ echo $HOME            show home directory
```
```sh
$ echo $USER            show user name
```
* _these are from environment variables_

```sh
$ env           show environment variables
```
_One particularly important variable is the ```PATH```Variable._

```sh
$ echo $PATH                  PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
``` 
_Paths separated by colons ```:``` are the locations where your system looks for a command when it executes it._



## **cut**
```crtl_v + tab``` for use tab in terminal
_At the first create this file:_
```sh
$ echo 'The quick brown; fox jumps over the lazy  dog' > sample.txt                 write text, and create file and copy text on it
```

* To extract contents by a list of characters use ```-c```

```sh
$ cut -c 5 sample.txt               outputs the 5th character in each line of the file
```

* To extract the contents by a field use ```-f```:
```sh
$ cut -f 2 sample.txt               output the 2nd field
```
   _Anything separated by a Tab is considered a field._

* with use flag ```-d```, determines optional separator(delimiter):
```sh
$ cut -f 1 -d ";" sample.txt        --> TAB delimiter wit ";" delimiter
```


## **paste**
```paste``` it merges lines together in a file

First create file:
```sh
$ echo 'The
quick
brown
fox' > sample2.txt
```
* ```paste``` Merges lines in parallel. This means that the first line of the first file is merged with the first line of the second file,...

* use flag ```-s``` instead of merge parallel it work sequencelly. means puts all the lines of a file in a row on a single line, with a separator (Tab by default) between them.
```sh
$ paste -s sample2.txt
```

* use ```-d``` fag  for change delimiter to something else like space 
```sh
$ paste -d ' ' -s sample2.txt
```

train:
```sh
$ echo 'apple                                   
orange                                            
banana' > f1.txt                                  
```
```sh
$ echo 'green
sweet
yellow' > f2.txt
```
```sh
$ paste f2.txt f1.txt
```



## **head**
By default, ```head``` shows the first ten lines of a file:
```sh
$ head /var/log/syslog
```
* use ```-n``` flag for modify the line count:
```sh
$ head -n 15 /var/log/syslog
```



## **tail**
By default, view the last 10 lines of a file.

```sh
$ tail /var/log/syslog
```
use ```-n``` flag for modify the line count:
```sh
$ tail -n 10 /var/log/syslog
```

* View real-time changes to a file with the ‍‍‍‍‍```-f``` flag(follow):
```sh
$ tail -f /var/log/syslog
```



## **expand** and **unexpand**
```expand``` displays the contents of the file by converting ```Tab``` to ```Space```:
```sh
$ expand sample.txt
```

```sh
$ expand sample.txt > result.txt            to save output in a file
```
* Use the ```-a``` flag to convert spaces to tabs:
```sh
$ unexpand -a result.txt
```



## **join** and **split**
```join``` allows to join multiple files together by a common field.
_Create this files:_
```sh
file1.txt
1 John
2 Jane
3 Mary

file2.txt
1 Doe
2 Doe
3 Sue
```
```sh
$ join file1.txt file2.txt               in this case the files are joined via 1, 2, 3 field
```

```sh
file1.txt
John 1
Jane 2
Mary 3

file2.txt
1 Doe
2 Doe
3 Sue
```
```sh
$ join -1 2 -2 1 file1.txt file2.txt                -1 refers to file1.txt, -2 refers to file2.txt(in file1.txt first field, in file2.txt second field)
```

* with ```split``` , split a file up into different files 
```sh
$ split somefile
```



## **sort**
```sort``` is useful for sorting lines.

```sh
ile1.txt
dog
cow
cat
elephant
bird
```
```sh
$ sort file1.txt
```

* Do a reverse sort by ```-r```:
```sh
$ sort -r file1.txt
```

* Sort via numerical value by ```-n```:
```sh
$ sort -n file1.txt
```



## **tr** (Translate)

The ```tr``` allows to translate a set of characters into another set of characters.
```sh
$ tr a-z A-Z

hello   --->    HELLO
```



## **uniq** (Unique)
have a file with duplicates data, and want to remove duplicates. use ```uniq```.
```sh
reading.txt

book
book
paper
paper
article
article
magazine
```
```sh
$ uniq reading.txt
```

* by ```-c--- count of how many occurrences of a line:
```sh
$ uniq -c reading.txt
```

* by ```-u``` get unique values:
```sh
$ uniq -u reading.txt           --> magazine
```

* by ```-d``` get duplicate values:
```sh
$ uniq -d reading.txt
```

**Note** : _uniq does not detect duplicate lines unless they are adjacent. and for detect should be adjucent._

* To overcome this limitation of ```uniq``` we use ```sort``` in combination with ```uniq```:
```sh
$ sort reading.txt | uniq
```



## **wc** and **nl**
The ```wc``` (word count) command shows the total count of words in a file. lines, number of words and number of bytes
```sh
$ wc /etc/passwd             --> It display the number of lines                 number of words and                     number of bytes, respectively.
```

* To just see just the count of a certain field, use the ```-l```, ```-w```, or ```-c``` respectively.
```sh
$ wc -l /etc/passwd
```

* to check the count of lines on a file use ```nl```(number lines):
```sh
file1.txt
i
like
turtles
```
```sh
$ nl file1.txt
```



## **grep**
 It allows you to search files for characters that match a certain pattern. 
 ```sh
 $ grep fox sample.txt
 ```

 * ```grep``` **patterns** that are case insensitive with the ```-i``` flag: 
 ```sh
 $ grep -i somepattern somefile
 ```

 * can combine ```grep``` with other commands with ```|```:
 ```sh
 $ env | grep -i User
 ```

 * use regular expressions in your pattern: 
 ```sh
 $ ls /somedir | grep '.txt$'           -->     Should return all files ending with .txt in somedir
 ```

 ## **End Text-Fu** ##