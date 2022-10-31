# Lab Report 3

## find options
### (1) -iname 
```
find Y -iname X
```
can find all the files whose name is X and contains both capital and small letters in the directory Y. It is very useful when you forgot the name's capital. This option is useful because if you forget the letter case of the file name, it can still help you find it.
Examples 1:
Find the file chapter-1.txt contains both capital and small letters in the folder technical.
The result is returning the file with the name of chapter-1.txt contains both capital and small letters in the folder technical. Same as expected.
```
find technical -iname chapter-1.txt
```
![Image](https://sara0112.github.io/cse15l-lab-reports/Lab3_01.png)

Examples 2:
Find the file ChAPtER-1.txt contains both capital and small letters in the folder technical.
The result is returning the file with the name of ChAPtER-1.txt contains both capital and small letters in the folder technical. Same as expected.

```
find technical -iname ChAPtER-1.txt
```
![Image](https://sara0112.github.io/cse15l-lab-reports/Lab3_02.png)

Examples 3:
Find the files contains "CH", including both capital and small letters, in the folder technical.
The result is returning the file with the name contains "CH", including both capital and small letters, in the folder technical. Same as expected.

```
find technical -iname "CH*"
```
![Image](https://sara0112.github.io/cse15l-lab-reports/Lab3_03.png)


### (2) -type 
