# Lab Report 4 - Vim

## Part 1
### (1) 
Using vim to open DocSearchServer.java in terminal. 
```
vim DocSearchServer.java<Enter>
```
The image below shows the code of DocSearchServer.java in the terminal.

![Image](https://sara0112.github.io/cse15l-lab-reports/lab4_01.png)

### (2)
Finding all "start" in the DocSearchServer.java by using 
```
:%s/start/<Enter>
```
The image below shows that the first "start" is found.

![Image](https://sara0112.github.io/cse15l-lab-reports/lab4_02.png)

### (3)
Replacing all "start" to "base" in the DocSearchServer.java by using 
```
:%s/start/base/g<Enter>
```
The image below shows that all "start" are replaced to "base".

![Image](https://sara0112.github.io/cse15l-lab-reports/lab4_02.png)

## Part 2
### (1) Make edit in Visual Studio Code -> upload file to remote server -> run the test
Start in Visual Studio Code to replace all "start" to "base" in DocSearchServer.java, then scp DocSearchServer.java to the remote server and run bash test.sh on the remote to test it out. This way takes 80.19s.

### (2) Log in the remote server -> using Vim to make edit -> run the test
Start already logged into a ssh session. Then, replace all "start" to "base" in DocSearchServer.java in Vim, then exit Vim and run bash test.sh. This way takes 68.44s.

### (3) Which of these two styles would you prefer using if you had to work on a program that you were running remotely, and why?
I prefer using the second method because it is faster. If I change only one file, this method is the most convenient to make changes and test remotely.

### (4) What about the project or task might factor into your decision one way or another? (If nothing would affect your decision, say so and why!)
If I need to modify multiple files at the same time to fix a bug, I think it is most convenient to test them on the local server and then upload all of them together.