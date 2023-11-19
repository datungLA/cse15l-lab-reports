# Lab Report 4 - Vim (Week 7)
## Step 4 (log in ieng6)
![image](https://github.com/datungLA/cse15l-lab-reports/assets/97591324/98ad1909-d35d-4bb9-823d-650fe1f3746b)
In this step, I first open my computer terminal and run the command below: \
`ssh cs15lfa23qt@ieng6.ucsd.edu`
## Step 5 (clone repo)
![image](https://github.com/datungLA/cse15l-lab-reports/assets/97591324/a8dafe18-c177-4c60-b9c9-6c324ad87427)
In this step, I clone the repo with SSH as shown in the command below: \
`git clone git@github.com:datungLA/lab7.git` 

## Step 6 (run test.sh)
![image](https://github.com/datungLA/cse15l-lab-reports/assets/97591324/b75a4579-f73b-4471-bc14-953765f9b8ca)
In this step, I make sure that I am in the directory that contains the test.sh script file. However, I was at the home directory. Therefore, I run the command below to go in lab7 directory: \
`cd lab7` \
Since I am now in the right directory, I run this command to run test.sh script file: \
`bash test.sh`
## Step 7 (edit .java file to fix bug)
![image](https://github.com/datungLA/cse15l-lab-reports/assets/97591324/e760e22f-c97f-4070-8e75-506c4dd788b7)
In this step, I simply run the command: `vim ListExamples.java` to open ListExamples.java file under vim mode as I am in the same directory as the file. \
![image](https://github.com/datungLA/cse15l-lab-reports/assets/97591324/37995ab7-b78d-4bdd-a55c-8a74f1c1f144)
In this step, there are multiple key combinations to perform different tasks \
Here are the combinations of key pressed and their functions: 
1) Key pressed: `<shift> <;>`\
   Function: this combination will open the command-line modes.
2) Key pressed: `<shift> </> <i> <n> <d> <e> <x> <1> <enter>` \
   Function: this combination will help me type `?index1` in the command-line. This searches for `index1` first encounter from bottom up and moves the cursor to the beginning of the word.

![image](https://github.com/datungLA/cse15l-lab-reports/assets/97591324/0c8d3e87-c6d5-47b8-abdb-b03a9a6e7258)
Luckily, the first search brings me to the faulty variable that needs to be fixed. \
In this step, there are multiple key combinations to perform different tasks \
Here are the combinations of key pressed and their functions: 
1) Key pressed: `<i>`\
   Function: pressing key 'i' while in Normal Mode will put me into 'Insert' mode where I can edit the content in the file.
2) Key pressed: `<right> <right> <right> <right> <right> <right> <delete> <2>` \
   Function: this combination will move my cursor to the right 6 times. By this time, I press 'delete' key to erase the character 1 in index1 and press '2' to insert the character 2 which this should change the variable from 'index1' to 'index2'.
   
![image](https://github.com/datungLA/cse15l-lab-reports/assets/97591324/9da5fc68-d6f4-4a48-8a62-bd8f5863b416)
In this step, there are multiple key combinations to perform different tasks \
Here are the combinations of key pressed and their functions: 
1) Key pressed: `<esc>`\
   Function: This combination will exit the 'Insert' mode and return me to the 'Normal' mode. 
3) Key pressed: `<shift> <;>`\
   Function: this combination will open the command-line modes.
4) Key pressed: `<w> <q> <enter>` \
   Function: this combination will enter the command 'wq' which stands for write and quit. It also understand for save the changes and quit the file.
   
## Step 8 (re-run test.sh)
![image](https://github.com/datungLA/cse15l-lab-reports/assets/97591324/31ed1453-6d16-4842-a03f-92686690abff)
Since I am still in the right directory, I run this command to run test.sh script file: \
`bash test.sh`

## Step 9 (git: staging-commit-push)
![image](https://github.com/datungLA/cse15l-lab-reports/assets/97591324/a40d3702-a4f9-40c3-bb0b-be5e8c47697d)
In this step, there are multiple entered commands to perform different tasks \
Here are the commands and their functions: 
1) Command: `git add .`\
   Function: this command will move newly modified files to the staging area.
2) Command: `git commit -m "finished 1m56s"`\
   Function: this command will move files from staging area to repository.
3) Command: `git push`\
   Function: this command will push changes to Github.
