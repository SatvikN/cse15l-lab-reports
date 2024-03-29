# Lab Report 5

## Debugging Scenario
**Student Post**<br/>
Hi, I am having a bug with my autograder when I try to run it on a server. I am using `java GradeServer 4040` to start the server. When I run the server using `curl` and the localhost url the server itself seems to be running fine.<br/><br/>
<img width="537" alt="pic 1" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/9f3ffc17-1820-4e0e-9977-9609dca9fb8d"><br/><br/>
I then tried to test my autograder by providing a Github URL containing java code for the script to grade. I have found that for some URLs the autograder works as expected but for others there seems to be an issue where the code gets compiled properly but the JUnit tests aren't being properly run. In the screenshot below it shows the autograder testing code that has the wrong filename. Here it properly clones the repository but prints that ListExamples.java file was not found which is the correct result.<br/><br/>
<img width="453" alt="pic 2" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/b7b1453d-ffba-4ad7-9e24-cef561bf118f">
<img width="929" alt="pic 3" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/5e704237-2d0d-423f-9b68-5f4ee89936d6"><br/><br/>
However, in the next screenshot the autograder is testing code with the correct implemntation so I expect it to pass all the tests. The autograder properly clones the repository, finds the file, and compiles the code. After doing this it is then supposed to run the JUnit tests but instead the autograder gives an error saying it couldn't find the necessary `.jar` files required to run the tests from the `TestListExamples.java` file.<br/><br/>
<img width="941" alt="pic 4" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/df67e161-657a-4393-8009-fec69b92bbc7"><br/><br/>
I believe that the error must be occuring in the final line of my `grade.sh` bash script where I use `java` to run the JUnit tests. All the above lines seem to be run properly because we the autograder prints "Program compiled successfully" which is the second to last line of code in `grade.sh`. However, I do not see any error in the line where I use the `java` function. I have already assigned the `CPATH` variable at the top to the path of the `.jar` files: `.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar`. I also include `org.junit.runner.JUnitCore` in the `java` function which is the class needed to run JUnit tests from the command line so I don't see a problem there. The name of the file containg the tests also looks to be correct. The `TestListExamples.class` file is supposed to be run by the `java` command and the file `TestListExamples.java` is getting properly compiled earlier in the shell script to create the `.class` file. Do you have any idea of what could be the issue with my autograder? I have included by `grade.sh` file below for reference and I believe the error is being caused by lines towards the end of the file.<br/><br/>
<img width="468" alt="pic 5" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/5525ec7b-dc80-484d-949a-c8c35cc597c7"><br/>

**TA Response**<br/>
Hi, thank you for all the context you provided regarding your bug. You are right that you have correctly assigned the `CPATH` variable and are correctly using the `org.junit.runner.JUnitCore` to run the JUnit tests. However, even though you have declared the file that contains the `.jar files` how will the java file know to reference that specific path?
You are correct that the error is at the end of your `grade.sh` file, and specifically it is in the `java` command.

**Student Response**<br/>
Thanks for the information. I believe I attempted to fix the bug by including `$CPATH` as an argument to the `java` function. I have now changed the last line to be `java $CPATH org.junit.runner.JUnitCore TestListExamples`. Since `CPATH` stores the path to the `.jar` files: `.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar`, the `java` command should now know where to find the `.jar` files.

I am still recieving an error, but it has changed slightly. The bug that I have been trying to fix is that the `java` function is unable to find the classpath that contains the necessary libraries to executing the Java code to run the tests. This is because it is not correctly interpreting the `CPATH` variable that contains the path to the class. After my attempted fix, the `java` function is now looking for the corrrect path: `.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar`. However, it is still unable to find the nexessary `.jar` files.<br/><br/>

<img width="939" alt="pic 6" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/f45f4c40-eb59-4ca7-8c01-d7583ed30ed8"><br/>

**Information About the Setup**<br/>
The necessary file structure you must have for the relavent files related to this bug is:<br/>
(this is not all the files in this directory)<br/>
- `list-examples-grader`
  - `grade.sh`
  - `GradeServer.java`
  - `lib`
    - `hamcrest-core-1.3.jar`
    - `junit-4.13.2.jar`

Contents of each file before fixing the bug:<br/>
`grade.sh`<br/><br/>
<img width="468" alt="pic 5" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/5525ec7b-dc80-484d-949a-c8c35cc597c7">

`GradeServer.java`<br/><br/>
<img width="429" alt="pic 8" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/6b4eb9c8-e778-4c84-a184-4ccbbc116a6b">

Command lines run to trigger the bug:<br/>
* `java GradeServer 4040`
  * Starts the server at port 4040
* `curl "http://localhost:4040/grade?repo=https://github.com/ucsd-cse15l-f22/list-methods-corrected"`
  * communicates with the server by specifying a URL with the necessary data
  * `http://localhost:4040` is the base url to retrieve data from
  * `/grade` is the path that the request is being sent to
  * `repo=https://github.com/ucsd-cse15l-f22/list-methods-corrected` specifies the query sent to the server. Here, the parameter `repo` is being assigned the value `https://github.com/ucsd-cse15l-f22/list-methods-corrected`

Edits to fix the bug:<br/>
* The last line in the `grade.sh` shell script needs to be changed from `java org.junit.runner.JUnitCore TestListExamples` to `java -cp $CPATH org.junit.runner.JUnitCore TestListExamples`
* Buy using `-cp $CPATH` it tells Java to use the specific classpath defined in the variable `CPATH`.
* If you don't use `-cp` in the `java` function, then the it will use the default class path, not the path stored in `CPATH`. So `-cp` needs to be used so that it looks for the `.jar` file in the `/lib` directory.

## Reflection
Some things I learn from lab during the second half of this quarter are how to use `vim` and `nano` to moddify files directly from the terminal without needing an external application. The vast functionality and commands within these editor make them very efficient to use and they can help you make quick edits when working on a project.

Another interesting I learned during lab is that Github deprecated the use of passwords for authentication for command-line processes. This was done in an attempt to increase security so now Github requires the use of ssh keys in order to authenticate operations you perform.
