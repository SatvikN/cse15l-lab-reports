# Lab Report 1

## Command: cd

**No Arguments**\
<img width="259" alt="pic1" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/c8f7b2dd-7905-4f5e-8e79-66d0d04a3aa0">
* The intial working directory is `/home/lecture1`
* After running the cd command with no arguments the filesystem's working directory gets reset back to the home directory which is just `/home`. This is because cd attempts to change the directory and since no directory is specified it changes it back to the home directory.
* This output is not an error and is the expected behaviour.

**Path to a Directory as Argument**\
<img width="347" alt="pic2" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/0bea573d-2f17-49be-8872-77bd30d43c6f">
* The intial working directory is `/home`
* After running the cd command with a specified path to a directory as the argument, the working directory of the filesystem switches to the inputed directory which is `/home/lecture1/messages`.
* This output is not an error and is the expected behaviour.

**Path to a File as Argument**\
<img width="420" alt="pic3" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/6692994a-f5c8-40e7-a52f-93a63af8f25a">
* The intial working directory is `/home`
* After running the cd command with a specified path to a file as the argument, the filesystem tells us that the inputed argument is not a directory and the working directory does not change.
* This output is an error because the command cd stands for change directory and you can't change the directory to a file.

## Command: ls
**No Arguments**\
<img width="373" alt="pic4" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/69cbeede-2ca1-4aac-9e02-0e7b7972291a">
* The intial working directory is `/home/lecture1`
* After running the ls command with no arguments, the filesystem displays all of the files and subdirectories inside the current working directory.
* This output is not an error and is the expected behaviour.

**Path to a Directory as Argument**\
<img width="356" alt="pic5" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/9ebb4387-474e-45b2-88d5-2cc3315a44e9">
* The intial working directory is `/home`
* After running the ls command with a specified path to a directory as the argument, the filesystem displays all of the files and subdirectories within the specified directory.
* This output is not an error and is the expected behaviour.

**Path to a File as Argument**\
<img width="358" alt="image" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/0a1ecfcf-5de5-400c-8fb6-8235c2232858">
* The intial working directory is `/home`
* After running the ls command with a specified path to a file as the argument, the filesystem displays information about the given files. In this case the filesystem prints out the path to the file and the filename.
* This output is not an error and is the expected behaviour.

## Command: cat
**No Arguments**\
<img width="266" alt="pic7" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/10e4e2d3-756e-497f-99aa-2f8690cd3534">
* The intial working directory is `/home/lecture1`
* After running the cat command with no arguements, the filesystem reads the user input from the keyboard and prints it back to the screen. The command gets terminated if the user types `ctrl + c`.
* This output is not an error and is the expected behaviour, however the cat command has a lot more functionality if it is used with some argument.

**Path to a Directory as Argument**\
<img width="356" alt="pic8" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/e61e47b0-5f59-4d82-ae6e-5dc2494a57a7">
* The intial working directory is `/home`
* After running the cat command with a specified path to a directory as the argument, the filesystem says that the input is a directory and doesn't do anything else. This is because the cat command excpects a file that if can read and display to the user, but it can't perform these functions with a directory.
* This output represents an error because the cat command isn't meant to be used with directories.

**Path to a File as Argument**\
<img width="724" alt="pic9" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/6c1ece52-05a2-4e66-a170-154683f88fd1">
* The intial working directory is `/home`
* After running the cat command with a specified path to a file as the argument, the filesystem prints out the contents of the inputed file.
* This output is not an error and is the expected behaviour.
