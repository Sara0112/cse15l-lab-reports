# Lab Report 3

## find options
### (1) -iname 
```
find Y -iname X
```
can find all the files whose name is X and contains both capital and small letters in the directory Y. This option is useful because if you forget the letter case of the file name, it can still help you find it.
#### Examples 1:
Find the file chapter-1.txt contains both capital and small letters in the folder technical.
The result is returning the path of the file with the name of chapter-1.txt contains both capital and small letters in the folder technical. Same as expected.
```
find technical -iname chapter-1.txt
```
![Image](https://sara0112.github.io/cse15l-lab-reports/lab3_01.png)

#### Examples 2:
Find the file ChAPtER-1.txt contains both capital and small letters in the folder technical.
The result is returning the path of the file with the name of ChAPtER-1.txt contains both capital and small letters in the folder technical. Same as expected.

```
find technical -iname ChAPtER-1.txt
```
![Image](https://sara0112.github.io/cse15l-lab-reports/lab3_02.png)

#### Examples 3:
Find the files contains "CH", including both capital and small letters, in the folder technical.
The result is returning the path of the files with the name contains "CH", including both capital and small letters, in the folder technical. Same as expected.

```
find technical -iname "CH*"
```
![Image](https://sara0112.github.io/cse15l-lab-reports/lab3_03.png)


### (2) -type 
Determine the type to look for. For example -type d means directory, -type f means file.
It is useful since when a file and a folder has the same name X in the folder Y and you only need to find the folder X, so you need to use the code below to find it.
```
find Y -type d -name X
```
#### Examples 1:
Find the file chapter-1.txt in the folder technical.
The result is returning the file path of chapter-1.txt. Same as expected.
```
find technical -type f -name chapter-1.txt
```
![Image](https://sara0112.github.io/cse15l-lab-reports/lab3_04.png)
#### Examples 2:
Find the folder 911report in the folder technical.
The result is returning the folder path of 911report. Same as expected.
```
find technical -type d -name 911report
```
![Image](https://sara0112.github.io/cse15l-lab-reports/lab3_05.png)
#### Examples 3:
Find the files contains "CH", including both capital and small letters, in the folder technical.
The result is returning the path of the files with the name contains "CH", including both capital and small letters, in the folder technical. Same as expected.
```
find technical -type f -iname "CH*"
```
![Image](https://sara0112.github.io/cse15l-lab-reports/lab3_06.png)

### (2) -empty
find the empty file or folders. It is important because when you want to clean up some files or folders with size 0, you can use this to find them first and then delete them.
#### Examples 1:
Find the empty files in the folder technical.
The result is returning nothing because there is no empty files in the folder technical. Same as expected.
```
find technical -type f -empty
```
![Image](https://sara0112.github.io/cse15l-lab-reports/lab3_07.png)
#### Examples 2:
I make a empty file called empty-1.txt in the folder technical. 
Find the empty files in the folder technical.
The result is returning the path of empty-1.txt. Same as expected.
```
find technical -type f -empty
```
![Image](https://sara0112.github.io/cse15l-lab-reports/lab3_08.png)
#### Examples 3:
I make a empty folder called empty-folder in the folder technical. 
Find the empty folders in the folder technical.
The result is returning the path of empty-folder. Same as expected.
```
find technical -type d -empty
```
![Image](https://sara0112.github.io/cse15l-lab-reports/lab3_09.png)