# Lab Report 2

## Part 1

**Code for ChatServer**<br /><br />
![pic1](https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/7b1d1a59-d871-487e-a658-4f837e41fd71)

**Using `/add-message`**<br /><br />
<img width="1440" alt="pic2" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/557d3240-6d09-4b40-98b0-03664a5d0047">

Which methods in your code are called?
What are the relevant arguments to those methods, and the values of any relevant fields of the class?
How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

* First, the main method in the ChatServer class is called and later the handleRequest method gets called.
* The arguments for the main method are only a single command line argument that is provided by the user. This argument represents the port that the server will be created on. The only relavent field in the ChatServer class is the `int` representing the port. It has a value of 4000.
* The handleRequest method also has only argument which is the url. The url has a value of `https://0-0-0-0-4000-bnbfsj00dbk4k5qv8e2r8mtiho.us.edusercontent.com/add-message?s=Hello!&user=jpolitz` which was entered into the web browser.

<img width="1440" alt="pic3" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/ea8ca23a-79b3-4132-9542-60c2c1eb664a">

## Part 2

## Part 3
