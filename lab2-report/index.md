# Lab Report 2 - Servers and SSH Keys (Week 3)
# Part 1
# 1st /add-message

<img width="1407" alt="serverOutput1" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/27a44fd1-4327-4ec6-a546-fb4e88a34bb7">

## Methods called:
Two methods are called when the page is accessed which are method `handle` from ServerHttpHandler class and method `handleRequest` from Handler class.
## Relevant arguments:
For ServerHttpHandler.handle(...), the relevant argument is `exchange`, specifically exchange.getRequestURI() which would be http://localhost:port/add-message?s=cse15l \
For Handler.handleRequest(...), the relevant argument is `url` which would be the same as exchange.getRequestURI() from above.
## Changes:
In Handler.handleRequest(...), the num is incremented from 3 to 4.\
The str in Handler class gets appended with "4: cse15l\n".

# 2nd /add-message
![Image](serverOutput2.png)
## Methods called:
Two methods are called when the page is accessed which are method `handle` from ServerHttpHandler class and method `handleRequest` from Handler class.
## Relevant arguments:
For ServerHttpHandler.handle(...), the relevant argument is `exchange`, specifically exchange.getRequestURI() which would be http://localhost:port/add-message?s=cse15l \
For Handler.handleRequest(...), the relevant argument is `url` which would be the same as exchange.getRequestURI() from above.
## Changes:
In Handler.handleRequest(...), the num is incremented from 4 to 5.\
The str in Handler class gets appended with "5: datung\n".

# Code for stringServer

<img width="700" alt="Screenshot 2023-10-31 at 8 53 59 PM" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/47100da3-cd1c-4934-b7ba-753989f64be4">

# Part 2
a) The path to the private key for your SSH key for logging into ieng6 (on your computer or on the home directory of the lab computer)\
`/Users/nickung/.ssh`
![Image](privateKeyPath.png)\
b) The path to the public key for your SSH key for logging into ieng6 (within your account on ieng6)\
`/home/linux/ieng6/cs15lfa23/cs15lfa23qt/.ssh`
![Image](publicKeyPath.png)\
c) A terminal interaction where you log into ieng6 with your course-specific account without being asked for a password.
![Image](terminalInteraction.png)
# Part 3
In a couple of sentences, describe something you learned from lab in week 2 or 3 that you didn’t know before.\
In week 3, I was able to learn that adding a . before the name of a file will make the file hidden. I believe this is useful to keep important files hidden preventing unwanted changes made to those files. In addition to that, the ls command can also take an argument namely -a that will show hidden files. Therefore, it is a great tool to see what is hidden.
