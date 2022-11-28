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
![Image](https://sara0112.github.io/cse15l-lab-reports/lab5_1.png)

### (2) Example of https://github.com/ucsd-cse15l-f22/list-methods-filename
![Image](https://sara0112.github.io/cse15l-lab-reports/lab5_2.png)

### (3) Example of https://github.com/ucsd-cse15l-f22/list-methods-compile-error
![Image](https://sara0112.github.io/cse15l-lab-reports/lab5_3.png)

##  Trace the Script of the Example of https://github.com/ucsd-cse15l-f22/list-methods-filename
