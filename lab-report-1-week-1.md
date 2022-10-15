# Lab Report 1 Week 1

## 1.Installing VScode
Go to the Visual Studio Code website https://code.visualstudio.com/. Follow the instructions to download and install it. 

![Image](https://sara0112.github.io/cse15l-lab-reports/Lab1_01.png)

## 2.Remotely Connecting
Open a terminal in VSCode.  Using ssh remote connect to ieng6 sever.

![Image](https://sara0112.github.io/cse15l-lab-reports/Lab1_02.png)

## 3.Trying Some Commands
Try to run some commands below.  
cd ~ : this command is used to change directory to the home directory.  
cd : this command also work same as cd ~ command.  
ls -a : this command list all files including hidden files.    
ls -lat : this command long lists all the directories and file names by sorting the modified date in reverse order.  
cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/ : this command copy file "/home/linux/ieng6/cs15lfa22/public/hello.txt" to current diractory.  
cat /home/linux/ieng6/cs15lfa22/public/hello.txt : this command show content of given filename "/home/linux/ieng6/cs15lfa22/public/hello.txt".  

![Image](https://sara0112.github.io/cse15l-lab-reports/Lab1_03.png)

## 4.Moving Files with scp
Create a file on client computer called WhereAmI.java and put in code below.  
```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```   
Go to the directory of WhereAmI.java and using "scp" to copy WhereAmI.java to server.
```
scp WhereAmI.java senkhjargal@ieng6.ucsd.edu:~/
```
Go to server, type in
```
javac WhereAmI.java
java WhereAmI
```

![Image](https://sara0112.github.io/cse15l-lab-reports/Lab1_04.png)
After type in 
```
javac WhereAmI.java
java WhereAmI
```
we can see that  
Linux : the operation system name.   
senkhjargal : the user name.  
/home/linux/ieng6/oce/74/senkhjargal : the user home directory.  
/home/linux/ieng6/oce/74/senkhjargal : the user current directory.  

## 5.Setting an SSH Key
Since every time we log in or run scp, we have to type our password. We use SSH Key to avoid this repetitive, frustrating task. Run "ssh-keygen" and press enters. This created two new files on your system; the private key (in a file id_rsa) and the public key (in a file id_rsa.pub), stored in the .ssh directory on your computer. Copy them to server .ssh folder. Try ssh again and you will find that you don't need to type password anymore.

![Image](https://sara0112.github.io/cse15l-lab-reports/Lab1_05_01.png)

The screenshot above shows that running "ssh-keygen", the identification file is generated and saved in "/Users/sara/.ssh/id_rsa" and the public key is generated and saved in "/Users/sara/.ssh/id_rsa.pub". Then, go to the server. 

![Image](https://sara0112.github.io/cse15l-lab-reports/Lab1_05_02.png)
The screenshot above shows that in the server, type in
```
mkdir .ssh
```
to create the folder .ssh and using 
```
ls -a
```
to check .ssh folder is been made. Then, go to the client and type in
```
scp /Users/sara/.ssh/id_rsa.pub senkhjargal@ieng6.ucsd.edu:~/.ssh/authorized_keys
```
and your password to copy the public key to the .ssh folder in server.   In the end, login to server again and this time, I don't need to type in password.  
Therefore, the problem solved!

## 6.Optimizing Remote Running
1. Try to write a command in quotes at the end of an ssh command to directly run it on the remote server, then exit. For example:
```
ssh senkhjargal@ieng6.ucsd.edu "ls"
```  
you can see all directories and files in server home will be printed.  
2. Try to use semicolons to run multiple commands on the same line in most terminals. For example:   
```
cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI
```
you can see that OtherMain.java is a copy version of WhereAmI.java and OtherMain.class is been generated. Also, WhereAmI is been run and you can see the result including operation system name, user name, user home directory and user current directory.  
3. Try to use the up-arrow on your keyboard to recall the last command that was run. For example,   
```
cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI
```
is the last command that was run. And I push the up-arrow, the command showed. 
![Image](https://sara0112.github.io/cse15l-lab-reports/Lab1_06.png)
