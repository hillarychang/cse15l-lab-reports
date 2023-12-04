# Lab Report 5

## Part 1

Student: Hi all, I'm currently working on a project, but I was encountering a strange issue. I've attached a screenshot of the error I'm getting, and I'd really appreciate some guidance with this!
 ![Image](bug.png)  
I'm using a bash script project.sh to compile and run a Java program with arrays. I'm not sure why, but it's throwing a strange error. 

TA: Hi, thank you for your EdStem post. To help you better, could you run the following command and share the output with me?
```./project.sh 1 2 3 4 5 2>&1```
This command uses 1, 2, 3, 4, and 5 as command-line arguments to run the program. The command redirects both standard output and standard error to the console. It will give us more information about what might be going wrong.

Terminal Output after Running the Command:
After running the ```./project.sh 1 2 3 4 5 2>&1 command```, it appears that the script is unable to find or load the main class MainClass.
```Error: Could not find or load main class MainClass```

Bug Description:
The bug is caused by the bash script run_project.sh failing to find or load the main class MainClass when attempting to run the Java program. This could be due to an issue with the classpath or the compilation process.

Setup Information:

File & Directory Structure:
ArrayExamples.java
MainClass.java
project.sh

ArrayExamples.java
public class ArrayExamples {
    static void reverseInPlace(int[] arr) {
        for (int i = 0; i < arr.length; i += 1) {
            arr[i] = arr[arr.length - i - 1];
        }
    }
}

project.sh
javac ArrayExamples.java MainClass.java
java MainClass 1 2 3 4 5

Command Line to Trigger the Bug:
```./run_project.sh```

Description of Fix:
To fix the bug, update the run_project.sh script to include the classpath when running the Java program.
```javac MainClass.java```
```java -cp . MainClass```

This modification ensures that the classpath includes the current directory when running the Java program. After making this change, the script should successfully compile and execute the MainClass without the error.

## Part 2
Run the tests, demonstrating that they fail
Keys pressed: ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```cd lab7```
```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```chmod +x```
```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```<up>``` ```./test.sh```

The git clone command was 8 up in the search history, so I used 8 up arrows to access it. Before that, I used 10 up arrows to cd into the lab7 directory (that contains ListExamples.java), and 9 up arrows to give myself execute permission to the file.  
 ![Image](second.png)  
