# Lab Report 5

## grade.sh

```
set -e

CPATH=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

rm -rf student-submission
git clone $1 student-submission 
cp TestListExamples.java student-submission
cp -r lib student-submission

cd student-submission

if test -e ListExamples.java 
then 
    echo "  Has ListExamples.java"
else
    echo "  Missing ListExamples.java" 
    exit 1
fi

if javac -cp $CPATH *.java 
then 
    echo "  Compiled  " 
    if java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > testListExamples.txt 
    then
        RESULT="$(sed -n 2p testListExamples.txt)"
        NUMBER="${RESULT//[^E]}"
        echo "  There were " ${#NUMBER}  " failures" 
    else
        RESULT="$(sed -n 2p testListExamples.txt)"
        NUMBER="${RESULT//[^E]}"
        echo "  There were " ${#NUMBER}  " failures" 
        exit 1
    fi
else
    echo "  Compile error"
    exit 1
fi
```

## Examples
Screenshots of three different student submissions and their reported grade as loaded in the browser (URL like https://localhost:4000/grade?repo=https://github.com...)

### (1) Example of https://github.com/ucsd-cse15l-f22/list-methods-lab3
It is an example can be compiled but there is no full credit. 
![Image](https://sara0112.github.io/cse15l-lab-reports/lab5_1.png)

### (2) Example of https://github.com/ucsd-cse15l-f22/list-methods-filename
It is an example missing ListExamples.java in student-submission folder. 
![Image](https://sara0112.github.io/cse15l-lab-reports/lab5_2.png)

### (3) Example of https://github.com/ucsd-cse15l-f22/list-methods-compile-error
It is an example with compile error. 
![Image](https://sara0112.github.io/cse15l-lab-reports/lab5_3.png)

##  Trace the Script of the Example of https://github.com/ucsd-cse15l-f22/list-methods-filename
```
set -e # stop execution

CPATH=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" # declared variable

rm -rf student-submission # remove the current "student-submission"
git clone $1 student-submission # clone a student-submission folder from $1 
cp TestListExamples.java student-submission # copy TestListExamples.java to student-submission folder
cp -r lib student-submission # copy lib folder to student-submission folder

cd student-submission # go into student-submission folder

if test -e ListExamples.java # In this case, test return false since there is no ListExamples.java in student-submission folder. 
then 
    echo "  Has ListExamples.java" 
else
    echo "  Missing ListExamples.java" # In this example, showing Missing ListExamples.java
    exit 1
fi
```
