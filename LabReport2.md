# Lab Report 2

## Part 1 - ChatServer

**Code for `ChatServer`**<br /><br />
![pic1](https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/7b1d1a59-d871-487e-a658-4f837e41fd71)

**Using `/add-message`**<br /><br />
<img width="1440" alt="pic2" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/557d3240-6d09-4b40-98b0-03664a5d0047">

* First, the main method in the `ChatServer` class is called and later the handleRequest method gets called.
* The arguments for the main method are only a single command line argument that is provided by the user. This argument represents the port that the server will be created on. The only relevent field in the `ChatServer` class is the `int` representing the port. It currently has a value of 4000.
* The handleRequest method also has only one argument which is the url that was entered into the web browser. The url has a value of `https://0-0-0-0-4000-bnbfsj00dbk4k5qv8e2r8mtiho.us.edusercontent.com/add-message?s=Hello!&user=jpolitz`. One important field in the `Handler` class is `String entireString`. This field holds the text of all the past chats that were entered into the web page.
* This request made to the web server has the effect of appending a new message to `entireString` based on the text in the url.

<img width="1440" alt="pic3" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/ea8ca23a-79b3-4132-9542-60c2c1eb664a">

* First, the main method in the `ChatServer` class is called and then the handleRequest method gets called.
* The arguments for the main method are only a single command line argument that is provided by the user. This argument represents the port that the server for the server. The value of `port` remains 4000 because that is the value assigned to it when the web server was started.
* The handleRequest method also has only one argument which is the url. The url has a value of `https://0-0-0-0-4000-bnbfsj00dbk4k5qv8e2r8mtiho.us.edusercontent.com/add-message?s=Hi!%20How%20are%20you%20doing&user=snayak` which was entered into the web browser. The `%20` text found in the url represents spaces. One field in the `Handler` class is `String entireString` which holds the text of all the past chats entered into the web page.
* This request made to the web server has the effect of appending an additional message to `entireString` based on the text in the url.

## Part 2 - SSH Keys

**Absolute path to the private key (on my machine)**<br /><br />
<img width="420" alt="pic4" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/432a1018-1285-4c7e-abc7-da71e666536c">

**Absolute path to the public key (on ieng6)**<br /><br />
<img width="478" alt="pic5" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/7d12312d-7205-49fb-91d7-47eff4b41f82">

**Logging into `ieng6` account without password**<br /><br />
<img width="752" alt="pic6" src="https://github.com/SatvikN/cse15l-lab-reports/assets/108087443/d612ecfe-a2cc-4297-b801-518e7f3ce870">

## Part 3 - Reflection
I learned how you could use ssh keys to save time connecting to a remote machine. In my previous work, it became very tedious to have to enter the same password so many times just to access a machine. Using ssh keys is simple to set up and very beneficial in the long run. Another thing I learned in lab during weeks 2 and 3 is how to launch a web server in Java. Learning how to build and run a server has given me a better understanding of what URLs actually mean. Previously URLs seemed kind of random but now I understand how the information within a URL is used in a search query.
