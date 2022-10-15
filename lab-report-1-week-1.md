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

## 5.Setting an SSH Key
Since every time we log in or run scp, we have to type our password. We use SSH Key to avoid this repetitive, frustrating task. Run "ssh-keygen" and press enters. This created two new files on your system; the private key (in a file id_rsa) and the public key (in a file id_rsa.pub), stored in the .ssh directory on your computer. Copy them to server .ssh folder. Try ssh again and you will find that you don't need to type password anymore.

![Image](https://sara0112.github.io/cse15l-lab-reports/Lab1_05_01.png)
![Image](https://sara0112.github.io/cse15l-lab-reports/Lab1_05_02.png)

## 6.Optimizing Remote Running
Try to write a command in quotes at the end of an ssh command to directly run it on the remote server, then exit. Try to use semicolons to run multiple commands on the same line in most terminals. Try to use the up-arrow on your keyboard to recall the last command that was run.

![Image](https://sara0112.github.io/cse15l-lab-reports/Lab1_06.png)
