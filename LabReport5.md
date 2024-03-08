# Lab Report 5

## Debugging Scenario
**Student Post**
Hi, I am having a bug with my autograder when I try to run it on a server. I am using `java GradeServer 4040` to start the server. When I run the server using `curl` and the localhost url the server itself seems to be running fine. (First screenshot below). I then try to test my autograder by providing a Github URL containing java code for the script to grade. I have found that for some URLs the autograder works as expected but for others there seems to be an issue where the code gets compiled properly but the JUnit tests aren't being properly run. In the second screenshot it shows the autograder testing code that has the wrong filename. Here it properly clones the repository but prints that ListExamples.java file was not found which is the correct result.
**TA Response**

**Student Response**


## Reflection
