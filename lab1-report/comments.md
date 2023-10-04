## Lab 1 Report
** For each of the commands cd, ls, and cat, and using the workspace you created in this lab:\ ** 

a) Share an example of using the command with no argument.\
`[user@sahara ~]$ cd`\
_cd does not make any change without an argument._\
```
[user@sahara ~]$ ls
lecture1
```
_ls will print all directories and files in the current working directory._\
```
[user@sahara ~]$ cat

```
_cat will cause the terminal to continuously run unless forced to stop when use without an argument._\
b) Share an exmaple of using the command with a path to a directory as an argument.\
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$
```
_cd will change the current working directory to given directory when cd is called_\
```
[user@sahara ~/lecture1]$ ls messages 
en-us.txt  es-mx.txt  vn-vi.txt  zh-cn.txt
```
_ls will print all directories and files in the given working directory._\
```
[user@sahara ~/lecture1]$ cat /home/lecture1
cat: /home/lecture1: Is a directory
```
_cat prints an error pointing the given argument is a directory  ._
c) Share an example of using the command with a path to a file as an argument.\
