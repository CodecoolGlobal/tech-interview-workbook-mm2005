# Web with Python questions


## Software design
### Clean code

1 Point out 5 suggestions, how to format an SQL query!
    1. alignment: each row strats with a new keyword (SELCET, FROM, JOIN, WHERE, etc.), keywords are written with CAPITAL letters
	2. if there are multiple arguments after a keyword, write the arguments in separate rows
	3. each line ends with a comma	
	4. indentation: use indentation for new lines without a keyword
	5. use comments (/* ... */), but not too much, only if really necessary
	+1: subqueries (CASE) should be placed in a new indented line
	
2 What layers can you name in a simple web application?
    1. Client
	2. Server
	3. Dynamic HTML pages
	4. Services (js)
	5. DataBase (+API calls)
	

### Error handling
3 What error can occur, when an array does not have an element on the requested index?
    ListIndexOutOfRange error
    
4 What is the “finally” block, and how would you use it?
    "try" block can with "catch" block and/or "finally" block.
	The finally-block will always execute after the try-block and catch-block(s) have finished executing.
	It always executes, regardless of whether an exception was thrown or caught.
	
5 Why should we catch special exception types?
    Catch-block is executed when any exception is thrown from within the try-block. Different exception types represent
    different states of the running program, which might require different actions (error handling) to be triggered. 


### Security
6 What is SQL injection? How to protect an application against it?
    Computer attack, where demaging code is submitted to a vulnerable program. The code is further submitted
    to the back-end database, executing unwanted actions.
	How to prtoect?
		- Escaping Special Characters: In SQL "string literals" (exp: a column of a table with STRING or VARCHAR data type) 
		  for example start and end where a delimiter is placed. In SQL, the standard delimiter is the single quote character – ‘.
		  Replace single quote with \' or a double quote with \".
		- Parameterized Queries: it means to pre-compile an SQL statement so that all you need to supply are the "parameters"
		  (think "variables") that need 			to be inserted into the statement for it to be executed.
		  Example: cur.execute("SELECT * FROM cars WHERE id=%(id)s", {'id': uid } )
		- Input Validation: it is to verify whether or not the type of input submitted by a user is allowed.
		- Table names, variables should be named randomly, so it will be hard to 'guess'.
		
7 What is XSS? How to protect an application against it?
8 How to properly store passwords?
    Never store passwords as plain text. Passwords should be hashed. Simple hashing is not enough, it should be salted.	
	Salted Password Hashing - We can randomize the hashes by appending or prepending a random string, called a salt,
	to the password before hashing, so that when the same password is hashed twice, the hashes are not the same.
	It is important that each user's password is hashed with a different salt.
	Concrete steps:
		- Generate a long random salt.
		- Prepend the salt to the password and hash it with a standard password hashing function like Argon2, bcrypt, scrypt, or PBKDF2.
		- Save both the salt and the hash in the user's database record.
		
9 What is HTTPS?
    Hypertext transfer protocol secure (HTTPS) is the secure version of HTTP.
	HTTPS uses an encryption protocol to encrypt communications. The protocol is called Transport Layer Security (TLS).
	This protocol secures communications by using what’s known as an asymmetric public key infrastructure.
	This type of security system uses two different keys to encrypt communications between two parties:
		- The private key - this key is controlled by the owner of a website and it’s kept, as the reader may have speculated, private.
		  This key lives on a web server and is used to decrypt information encrypted by the public key.
		- The public key - this key is available to everyone who wants to interact with the server in a way that’s secure.
		  Information that’s encrypted by the public key can only be decrypted by the private key.
	When a user connects to a webpage, the webpage will send over its SSL certificate which contains the public key necessary
	to start the secure session. The two computers, the client and the server, then go through a process called an SSL/TLS handshake,
	which is a series of back-and-forth communications used to establish a secure connection.
	
10 What is encryption and decryption?
    Encryption is the process of converting normal message (plaintext) into meaningless message (Ciphertext).
	Decryption is the process of converting meaningless message (Ciphertext) into its original form (Plaintext).
		
11 What is hashing?
    Hash algorithms are one way functions. They turn any amount of data into a fixed-length "fingerprint" that cannot be reversed.
    They also have the property that if the input changes by even a tiny bit, the resulting hash is completely different.
    
12 What is the difference between encryption and hashing? When would you use which?
    Encrypted data can be decrypted with the appropriate key whereas hashed data can not be turned back to the original content.
    Hashing can be used for storing passwords,comparing two files for equality without opening them, 
	Encryption can be used for secure communication where the message should be readeble for the receiver (online payments, databases, emails).

13 What encryption methods do you know?
    Symmetric encryption: Symmetric encryption uses a single key to encrypt as well as decrypt data.
    The key needs to be shared with all authorized people.
	Asymmetric encryption: Also called public key cryptography, asymmetric encryption uses two separate keys—one public
	(shared with everyone) and one private (known only to the key’s generator).
	The public key is used to encrypt the data and the private key helps to decrypt it.
	Also:
		Advanced Encryption Standard (AES)
		Data Encryption Standard (DES)
		Rivest-Shamir-Adleman (RSA)
		Blowfish
		
14 What hashing methods do you know?
    folding method, mid-squares, division hashing, Fibonacci hashing
    
15 How/where would you store sensitive data (like db password, API key, ...) of your application?
    Rule #1 is NOT to hardcode passwords or crypto keys in your program.
	Also, do not store the developer credentials on the user's machine.
	One possibility: store data on the server's machine in the os.environment a configuration file.



## Computer science
### Algorithms

16 What is the difference between Stack and Queue data structure?
    STACK
		Stacks are based on the LIFO principle, i.e., the element inserted at the last, is the first element to come out of the list.
		Insertion and deletion in stacks takes place only from one end of the list called the top
		Insert operation is called push operation.
		Delete operation is called pop operation.
		In stacks we maintain only one pointer to access the list, called the top, which always points to the last element present in the list.
	QUEUE
		Queues are based on the FIFO principle, i.e., the element inserted at the first, is the first element to come out of the list.
		Insertion and deletion in queues takes place from the opposite ends of the list.
		    The insertion takes place at the rear of the list and the deletion takes place from the front of the list.
		Insert operation is called enqueue operation.
		Delete operation is called dequeue operation.
		In queues we maintain two pointers to access the list. The front pointer always points to the first element
		   inserted in the list and is still present, and the rear pointer always points to the last inserted element.
		   
17 What is BubbleSort? Describe the main logic of this sorting algorithm.
    Bubble Sort is the simplest sorting algorithm that works by repeatedly swapping the adjacent elements if they are in wrong order.
	def bubble_sort(arr):
	    def swap(i, j):
		arr[i], arr[j] = arr[j], arr[i]
	    n = len(arr)
	    swapped = True
	    x = -1
	    while swapped:
		swapped = False
		x = x + 1
		for i in range(1, n-x):
		    if arr[i - 1] > arr[i]:
		        swap(i - 1, i)
		        swapped = True
	    return arr

18 Explain the process of finding the maximum and minimum value in a list of numbers!
    Initialize values of min and max as minimum and maximum of the first element of the list.
    Starting from 2nd, compare each element with max and min, and change max and min accordingly
    (i.e., if the element is smaller than min then change min, else if the element is greater than max then change max,
    else ignore the element)
    
19 Explain the process of calculating the average value in an array of numbers!
    Sum up all the numbers and dived by the lenght of the array.
    
20 What is Big O complexity? Explain time and space complexity!
    Big O notation is the language used for talking about how long an algorithm takes to run.
        It's how we compare the efficiency of different approaches to a problem.
	With big O notation we express the runtime in terms of how quickly it grows relative to the input, as the input gets arbitrarily large.
	how quickly the runtime grows: 	It's hard to pin down the exact runtime of an algorithm.
	    It depends on the speed of the processor, what else the computer is running, etc.
	    So instead of talking about the runtime directly, we use big O notation to talk about how quickly the runtime grows.
	relative to the input: If we were measuring our runtime directly, we could express our speed in seconds.
	    Since we're measuring how quickly our runtime grows, we need to express our speed in terms of something else.
	    With Big O notation, we use the size of the input, which we call "nn." So we can say things like the runtime grows
	    "on the order of the size of the input" (O(n)O(n)) or "on the order of the square of the size of the input" (O(n^2)O(n2)).
	as the input gets arbitrarily large: Our algorithm may have steps that seem expensive when nn is small but
	    are eclipsed eventually by other steps as nn gets huge. For big O analysis, we care most about
	    the stuff that grows fastest as the input grows, because everything else is quickly eclipsed as nn gets very large.
	Space complexity: Sometimes we want to optimize for using less memory instead of (or in addition to) using less time.
	    Talking about memory cost (or "space complexity") is very similar to talking about time cost.
	    We simply look at the total size (relative to the size of the input) of any new variables we're allocating.
	    
21 Explain the process of calculating the average value in a linked list of numbers!
    The average is the sum divided by the count.


### Procedural
22 How the CASE condition works in SQL?
23 How the switch-case condition works in JavaScript?
24 How to achieve a switch-case-like structure in Python?
25 Explain variable scoping in Python!
26 What’s the difference between const and var in JavaScript?
27 How the list comprehension looks like in Python?
28 How the “ternary expression” looks like in Python?
29 How the ternary expression looks like in JavaScript?
30 How to import a function from another module in Python?
31 How to import a function from another module in JavaScript?

### Functional
32 What is recursion?
33 Write a recursive function which calculates the Fibonacci numbers!
34 How to store a function in a variable in Python?
35 List the ways of defining a callable logical unit in JavaScript!
36 What is an event listener? How to attach one?
37 How to trigger an event in JavaScript?
38 What is a callback function? Tell some examples of its usage.
39 What is a Python decorator? How does it work? Tell some examples of its usage.
40 What is the difference between synchronous and asynchronous execution?

## Programming languages

### SQL

41 How can you connect your application to a database server? What are the possible ways?
42 When do you use the DISTINCT keyword in SQL?
43 What are aggregate functions in SQL? Give 3 examples.
44 What kind of JOIN types do you know in SQL? Could you give examples?
45 What are the constraints in sql?
46 What is a cursor in SQL? Why would you use one?
47 What are database indexes? When to use?
48 What are database transactions? When to use?
49 What kind of database relations do you know? How to define them?
50 You have a table with an “address” field which contains data like “3525, Miskolc, Régiposta 9.” (postcode, city, street name and address). How would you query all records related to Miskolc?
51 How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?

### HTML & CSS

52 What’s the difference between XML, XHTML and HTML?
53 How to include a JavaScript file in a webpage?
54 How to include a CSS file in a webpage?
55 How to select an element using its id in CSS?
56 How to select elements using their class in CSS?
57 How to select elements which have the ‘alpha’ and ‘beta’ classes in CSS?
58 How to select all list items in all ordered lists on the page in CSS?
59 How to select elements using their attributes in CSS?
60 What are UX and UI?
61 Please list some points that an application should fulfill to have good UX.
62 What is XML, XSLT, DTD?
63 What is the difference between HTML and XML?

### Javascript

64 What is javascript?
65 When to use AJAX? Bring examples of its usage.
66 What is DOM and how to manipulate it from Javascript?
67 What are events and how/why to use them in Javascript?
68 What is event bubbling/capturing? How would you use it?
69 What is JSON and how do we use it?

## Software engineering

### Version control

70 What type of branching strategy would you use?
71 What would you do if you find a bug on the production code (master branch)?
72 How can you move changes from one branch to another in GIT?
73 How does a VCS help with code reviews?
74 What is your favorite git command? Why?
75 What does remote/local mean in Git? 

### DevOps

76 Why is it good to use a package manager software?
77 Why is it good to use a virtual environment for a project?

### Networks

78 What kind of HTTP status codes do you know?
79 What is a API?
80 What is REST API?
81 What is JSON? When to use?
82 What is TCP/IP? What layers does it define, what are they responsible for?
83 What’s the difference between TCP and UDP?
84 How does an HTTP Request look like? What are the most relevant HTTP header fields?
85 How does an HTTP Response look like? What are the most relevant HTTP header fields?
86 What is DNS? How does it work?
87 What is a web server?
88 Explain the client-server architecture.
89 What would you use a session for?
90 What would you use a cookie for?

## Software Development Methodologies

91 What kind of software development methodologies do you know? What are the main features of these?
92 What are the SCRUM roles?
93 What are the SCRUM ceremonies?
94 What are the SCRUM artifacts?
95 What is the main goal of a retrospective meeting?
96 Explain, when would you recommend to use the waterfall methodology?
