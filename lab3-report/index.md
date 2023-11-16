# Lab Report 3 - Bugs and Commands (Week 5)
# Part 1 - Bugs
## Choose one of the bugs from week 4’s lab.
## ArrayExamples.reversedInPlace()
Provide:\
A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)
```
@Test
public void testReverseInPlaceWithMoreElements() {
  int[] input1 = { 1, 2, 3, 4, 5, 6 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[] { 6, 5, 4, 3, 2, 1 }, input1);
  System.out.println("testReverseInPlaceWithMoreElements passed");
}
```
An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
```
@Test
public void testReversedInPlaceWithOneElement() {
  int[] input1 = { 3 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[] { 3 }, input1);
}
```
The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)

<img width="762" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/d0513088-556a-4a0c-ba55-08ef5f16de92">

The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
before
```
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for (int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
after:
```
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for (int i = 0; i < arr.length / 2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
```
JUnit tests after code change:

<img width="725" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/3f17004f-01d5-45f1-a446-1e749e189e1e">

Briefly describe why the fix addresses the issue.\
The fix addresses the issue because this method simply reverse the elements in the array which can be done by swapping between two elements. Therefore, the number of iterations should only be half of the array length. In addition, a new variable called temp is added to hold the element at index i to replace element at index array length - i - 1 which the original method does not implement. Thus, only one element was replaced which the swap is not complete. This is the main bug in the program.

# Part 2 - Researching Commands
## find 
## -exec
`find technical/biomed/ -name "*.txt" -exec wc -l {} \;`

<img width="650" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/8d68614d-240b-4eec-9230-51502bf9e562">

the `-exec` flag allows the user to execute a command on each file found by `find`. In this case, each file found will come with the number of lines in that file which can be very useful information for the user.

`find technical/biomed/ -name "*.txt" -exec grep -r "base pair" {} \;`

<img width="782" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/f5658e6c-629b-4cbf-8f4a-50552826f6c5">

In this case, in addition to the files found, `find` will also print the lines in each file found that contains the string "base pair".

##  -maxdepth -mindepth
`find technical -name "*.txt" -maxdepth 1`

<img width="683" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/0522f7b0-f517-4e3f-8f06-a5748f6d2cbd">

the `-maxdepth` flag allows the user to limit the depth of the directories that `find` will search. In this case, the maximum depth that find can search is 1 level below the current directory.

`find technical -name "*.txt" -mindepth 2`

<img width="455" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/ef254e1b-fa64-4c09-bae7-3f71a10a2abc">

the `-mindepth` flag allows the user to skip the number of levels below the current directory that `find` will search. In this case, the minimum depth will start finding 2 levels below the current directory.

## -mtime 
`find technical -name "*.txt" -mtime +30`

<img width="471" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/ea8e2b5c-2c19-4d19-ab12-2e107596ab1f">

the `-mtime` flag allows the user to find files that modified a specified time range. In this case, the user want to search for any .txt files that has been modified over 30 days. The over is represented as +30.

`find technical -name "*.txt" -mtime 0`

<img width="706" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/53edf930-db3a-4527-9259-e57c4048eff1">

In this case, the user want to search for any .txt files that has been modified within 24 hours that is strictly larger than 0 hours and less than 24 hours. This is different than -1 which can be equal to 24 hours.

## -type

`find technical -type d -iname "PLOS"`

<img width="586" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/79dae95e-0c3e-4904-be2b-43b5d0e847e0">

the `-type` flag allows the user to find files with a specific type such as directory or a normal file, etc. In this case, the user is asking for type `d` which is a directory.

`find technical -type f -iname "imlucky.txt"`

<img width="643" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/d8feb1d3-8be2-486d-b41c-5bd7e37504fb">

In this case, the user is asking for type `f` which is a normal file.

# Citations:
## Part 2 
## -type (Chatgpt: chat.openai.com)
`prompt: ` \
commands line options for type in unix \
`output: ` \
In Unix and Unix-like operating systems, the find command provides the -type option to specify the type of the file you are looking for. The -type option is followed by a single character that indicates the type of file. Here are the most commonly used file types you can specify with this option: \
Regular File (f): \
find . -type f searches for regular files. \
Directory (d): \
find . -type d searches for directories. \
Symbolic Link (l): \
find . -type l searches for symbolic links. \
... \
`altered/usage:` \
`find technical -type f -iname "imlucky.txt"` \
`find technical -type d -iname "PLOS"`

## -mtime (Chatgpt: chat.openai.com)
`prompt:` \
more interesting command lines option of find \
`output:` \
Find Files by Their Modification Time with -mtime, -atime, and -ctime: \
These options allow you to find files based on modification (-mtime), access (-atime), or inode change (-ctime) times. \
... \
`altered/usage:` \
`find technical -name "*.txt" -mtime +30` \
`find technical -name "*.txt" -mtime 0`

## -exec (Chatgpt: chat.openai.com)
`prompt:` \
more interesting command lines option of find \
`output:` \
The -exec option in the find command is a powerful feature that allows you to execute a command on each file that matches your find criteria. \
This capability extends the functionality of find from just locating files to performing actions on them. Here's a deeper look into how -exec works and some examples: \
... \
`altered/usage:` \
`find technical/biomed/ -name "*.txt" -exec wc -l {} \;` \
`find technical/biomed/ -name "*.txt" -exec grep -r "base pair" {} \;`

##  -maxdepth -mindepth (Chatgpt: chat.openai.com)
`prompt:` \
more interesting command lines option of find \
`output:` \
The -maxdepth and -mindepth options in the find command in Unix are used to control the depth of directories that the find command searches through. \
-maxdepth levels: This option limits the search to a specific number of directory levels below the command's starting point. For instance, -maxdepth 1 would restrict find to only look in the directory specified and not in any of its subdirectories. If you set -maxdepth 2, it would look in the specified directory and its immediate subdirectories, but no further. \
-mindepth levels: Conversely, this option tells find to ignore a certain number of directory levels before beginning to search. For example, -mindepth 1 would make find skip the starting directory and begin searching in its subdirectories. With -mindepth 2, the command would start searching from the subdirectories of the immediate subdirectories of the starting point. \
... \
`altered/usage:` \
`find technical -name "*.txt" -maxdepth 1` \
`find technical -name "*.txt" -mindepth 2`
