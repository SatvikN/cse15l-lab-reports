# Lab Report 5

## Debugging Scenario
**Student Post**
Hi, I am having a bug with my autograder when I try to run it on a server. I am using `java GradeServer 4040` to start the server. When I run the server using `curl` and the localhost url the server itself seems to be running fine. (First screenshot below). I then try to test my autograder by providing a Github URL containing java code for the script to grade. I have found that for some URLs the autograder works as expected but for others there seems to be an issue where the code gets compiled properly but the JUnit tests aren't being properly run. In the second screenshot it shows the autograder testing code that has the wrong filename. Here it properly clones the repository but prints that ListExamples.java file was not found which is the correct result.
However, in the next screenshot the autograder is testing code with the correct implemntation so I expect it to pass all the tests. The autograder properly clones the repository, finds the file, and compiles the code. After doing this it is then supposed to run the JUnit tests but instead the autograder gives an error saying it couldn't find the necessary `,jar` files required to run the tests from the `TestListExamples.java` file.
I believe that the error must be occuring in the final line of my `grade.sh` bash script where I use `java` to run the JUnit tests. All the above lines seem to be run properly because we the autograder prints "Program compiled successfully" which is the second to last line of code in `grade.sh`. However, I do not see any error in the line where I use the `java` function. I am using `$CPATH` as an argument to the java function and it stores the path to the `.jar` files: `'.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'`. I also include `org.junit.runner.JUnitCore` which is the class needed to run JUnit tests from the command line so I don't see a problem there. The name of the file containg the tests also looks to be correct. The `TestListExamples.class` file is supposed to be run by the `java` command and the file `TestListExamples.java` is getting properly compiled earlier in the shell script to create the `.class` file. Do you have any idea of what could be the issue with my autograder?

**TA Response**

**Student Response**


## Reflection
