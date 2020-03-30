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
    The case statement in SQL returns a value of specified conditions.
    Case expressions evaluate to the <result> of the first true <condition> similarly to a "IF-THEN-ELSE" statement.
    If there is no ELSE part and no conditions are true, it returns NULL.
    
23 How the switch-case condition works in JavaScript?
    Syntax
	switch(expression) {
	  case x:
	    // code block
	    break;
	  case y:
	    // code block
	    break;
	  default:
	    // code block
	}
	The switch expression is evaluated once. The value of the expression is compared with the values of each case.
	If there is a match, the associated block of code is executed.
	
24 How to achieve a switch-case-like structure in Python?
    if, elif, elif..., else
    
25 Explain variable scoping in Python!
    Scope Resolution in Python | LEGB Rule
	Namespaces : A namespace is a container where names are mapped to objects, they are used to avoid confusions
	in cases where same names exist in different namespaces. They are created by modules, functions, classes etc.
	Scope : A scope defines the hierarchical order in which the namespaces have to be searched.
	It is a context in which variables exist and from which they are referenced.
	It defines the accessibility and the lifetime of a variable.
	Scope resolution via LEGB rule :
	In Python, the LEGB rule is used to decide the order in which the namespaces are to be searched for scope resolution.
	The scopes are listed below in terms of hierarchy(highest to lowest/narrowest to broadest):
    	Local(L): Defined inside function/class
    	Enclosed(E): Defined inside enclosing functions(Nested function concept)
    	Global(G): Defined at the uppermost level
    	Built-in(B): Reserved names in Python builtin modules
	!!!!!!
	LEGB (local, enclosed, global, built-in) rule is to decide the order in which the namespaces are to be searched for scope resolution. The lifetime of a variable 	 is the duration for which the variable exists.
	A variable's lifetime starts when it's referenced, and ends at the end of the variable's scope.
	
26 What’s the difference between const and var in JavaScript?
    const is a variable which can't be overwritten, block scoped, cannot be reassigned
	var is editable, overwriteable, function scoped, can be reassigned
	
27 How the list comprehension looks like in Python?
    list = [i for i in range(n)]
    
28 How the “ternary expression” looks like in Python?
    [on_true] if [expression] else [on_false]
	min = a if a < b else b
	
29 How the ternary expression looks like in JavaScript?
    condition ? exprIfTrue : exprIfFalse
	let min = a < b ? a : b
	
30 How to import a function from another module in Python?
    from module import function
    
31 How to import a function from another module in JavaScript?
    1: Export the function from the "other_module" with the 'export' keyword
	2: import function from other_module
	
	
### Functional
32 What is recursion?
    Recursion is a method where a function calls itself once or more in its body.
    
33 Write a recursive function which calculates the Fibonacci numbers!
    def fio_num(i):
   		if i <= 1:
       			return i
		else:
		        return(fibo_num(i-1) + fibo_num(i-2))
		        
34 How to store a function in a variable in Python?
    def my_func(i):
	   	print(i)
	my_var = my_func
	
func call:
	my_var(42)
	
35 List the ways of defining a callable logical unit in JavaScript!


36 What is an event listener? How to attach one?
    An event listener looks for specified events, such as a click,
    mouseover, mouseenter, mouseleave, mousedown. Any DOM event can be attached to it.
	Syntax sample:
		let randomDomElement.addEventListener('click', myFunction);
		
37 How to trigger an event in JavaScript?
    element.dispatchEvent('eventName')
38 What is a callback function? Tell some examples of its usage.
    In JavaScript you can pass functions to other functions as variables.
	A JavaScript Callback Function is a function that is passed as a parameter to another JavaScript function, and the callback function is run inside of the function it was passed into.
	JavaScript Callback Functions can be used synchronously or asynchronously
	Example:
		function functionOne(x) { 
			alert(x); }
		function functionTwo(var1, callback) {
		    callback(var1);}
		functionTwo(2, functionOne);
		
39 What is a Python decorator? How does it work? Tell some examples of its usage.
    A decorator is a design pattern in Python that allows a user to add new functionality to an existing object
    without modifying its structure. Decorators are usually called before the definition of a function you want to decorate.
	- in Flask the app.route is used as decorator.
	
40 What is the difference between synchronous and asynchronous execution?
    Synchronous execution means the execution happens in a single series. A->B->C->D. If you are calling those routines,
        A will run, then finish, then B will start, then finish, then C will start, etc.
	When you execute something asynchronously, you can move on to another task before it finishes.
	    When a task is executed asynchronously, you can directly switch to another task before the previous has been completed.
	    One task does not depend on the other.
	

## Programming languages

### SQL

41 How can you connect your application to a database server? What are the possible ways?
    try:
	    connect_str = "dbname={} user={} host={} password={}".format(connection_data['dbname'],
	                                                                 connection_data['user'],
	                                                                 connection_data['host'],
	                                                                 connection_data['password'])
	    conn = psycopg2.connect(connect_str)
	    conn.autocommit = True
        except psycopg2.DatabaseError as e:
            print("Cannot connect to database.")
            print(e)
        else:
            return conn
            
42 When do you use the DISTINCT keyword in SQL?
    Each value of the column will appear once only.
    
43 What are aggregate functions in SQL? Give 3 examples.
    Aggregate functions group together values of multiple rows based on some kind of criteria.
	Examples: COUNT(), AVG(), SUM()
	
44 What kind of JOIN types do you know in SQL? Could you give examples?
    INNER JOIN: Only those cells returned which have values in both tables.
	LEFT JOIN: INNER JOIN values + those which has values on the left table, but not in. the right.
	    The cells without values (on the right) represented with NULLs.
	RIGHT JOIN: Same as LEFT JOIN but with the right table.
	FULL JOIN: INNER JOIN + cells from both tables which have values only one of them.
	
45 What are the constraints in sql?
    CREATE TABLE table_name (
    		column1 datatype constraint,
    		column2 datatype constraint,
    		column3 datatype constraint,
    		....
		);
	Constraints are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table.
	If there is any violation between the constraint and the data action, the action is aborted.
	EXAMPLES:
		NOT NULL - Ensures that a column cannot have a NULL value
		UNIQUE - Ensures that all values in a column are different
		PRIMARY KEY - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
		FOREIGN KEY - Uniquely identifies a row/record in another table
		
46 What is a cursor in SQL? Why would you use one?
    Cursor is a database object to retrieve data from a result set one row at a time, instead of other SQL commands
        that operate on all the rows in the result set at one time.
	We use cursor in SQL when we need to update records in a database table in singleton fashion means row by row.
	There are some conditions when we want to get record from one table and need to insert into another with performing some logic
	    or some conditions. It works as for/while loop.
	    
47 What are database indexes? When to use?
    Indexes are special lookup tables that the database search engine can use to speed up data retrieval.
        Simply put, an index is a pointer to data in a table. An index in a database is very similar to an index in the back of a book.
	An index helps to speed up SELECT queries and WHERE clauses, but it slows down data input, with the UPDATE and the INSERT statements.
	    Indexes can be created or dropped with no effect on the data.
	Creating an index involves the CREATE INDEX statement.
	
48 What are database transactions? When to use?
    A transaction is a unit of work that is performed against a database. A transaction is the propagation of one or more changes to the database.
    For example, if you are creating a record or updating a record or deleting a record from the table,
        then you are performing a transaction on that table. It is important to control these transactions to ensure the data integrity
        and to handle database errors.
	Properties of Transactions
		Transactions have the following four standard properties, usually referred to by the acronym ACID.
		Atomicity − ensures that all operations within the work unit are completed successfully.
		    Otherwise, the transaction is aborted at the point of failure and all the previous operations are rolled back to their former state.
		Consistency − ensures that the database properly changes states upon a successfully committed transaction.
		Isolation − enables transactions to operate independently of and transparent to each other.
		Durability − ensures that the result or effect of a committed transaction persists in case of a system failure.
	Transaction Control
		COMMIT − to save the changes.
		ROLLBACK − to roll back the changes.
		SAVEPOINT − creates points within the groups of transactions in which to ROLLBACK.
		
49 What kind of database relations do you know? How to define them?
    There are three specific types of relationships:
		one-to-one
		one-to-many
		many-to-many
	The tables participate in only one type of relationship at any given time.
	
50 You have a table with an “address” field which contains data like “3525, Miskolc, Régiposta 9.” (postcode, city, street name and address). How would you query all records related to Miskolc?
    SELECT *
	FROM table
	WHERE address = 'Miskolc';
	
51 How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?
    Transaction Control
	SAVEPOINT − creates points within the groups of transactions in which to ROLLBACK.


### HTML & CSS

52 What’s the difference between XML, XHTML and HTML?
    XML means eXtensible Markup Language, its method of representing data, so it can be send electronically and its machine independent.
	HyperText Markup Language, commonly referred to as HTML, used to write websites
	Extensible Hypertext Markup Language (XHTML) is a family of XML markup languages that mirror or extend versions
	of the widely used Hypertext Markup Language (HTML), the language in which Web pages are formulated.
	
53 How to include a JavaScript file in a webpage?
    <script src="{path/to/file.js}"></script>
    
54 How to include a CSS file in a webpage?
    <link rel="stylesheet" href="{path/to/file.css}">
    	
55 How to select an element using its id in CSS?
    #id{}
    
56 How to select elements using their class in CSS?
    .class{}
    
57 How to select elements which have the ‘alpha’ and ‘beta’ classes in CSS?
    .alpha.beta{}
    
58 How to select all list items in all ordered lists on the page in CSS?
    ol li{}
    
59 How to select elements using their attributes in CSS?
    example selects all <a> elements with a target="_blank" attribute:
		a[target="_blank"] {
		  background-color: yellow;
		}
		
60 What are UX and UI?
    UX design refers to the term “user experience design”, while UI stands for “user interface design”.
    User experience design is a human-first way of designing products. It is the process of developing and improving the quality
    of interaction between a user and all facets of a company.
	UI design considers the look, feel, and interactivity of the product. It’s all about making sure that the user interface of
	a product is as intuitive as possible, and that means carefully considering each and every visual, interactive element the user might encounter.
	Short: UI is for the good looking and UX is for the good usability.
		
61 Please list some points that an application should fulfill to have good UX.
    The ultimate purpose of UX design is to create easy, efficient, relevant, and all-round pleasant experiences for the user.
    
62 What is XML, XSLT, DTD?


63 What is the difference between HTML and XML?
    XML was designed to carry data - with focus on what data is
	HTML was designed to display data - with focus on how data looks
	XML tags are not predefined like HTML tags are

### Javascript

64 What is javascript?
    JavaScript is a scripting language that enables you to create dynamically updating content, control multimedia, animate images, and much more.
    The programs in this language are called scripts. They can be written right in a web page’s HTML and run automatically as the page loads.
    
65 When to use AJAX? Bring examples of its usage.
    AJAX stands for Asynchronous JavaScript and XML. (JSON) Twitter uses AJAX for showing notifictaions that there are new unread tweets.
    With AJAX you can modify the content of a webpage without the need of refreshing it.
	With AJAX, when you hit submit, JavaScript will make a request to the server, interpret the results, and update the current screen.
	In the purest sense, the user would never know that anything was even transmitted to the server.
	
66 What is DOM and how to manipulate it from Javascript?
    he Document Object Model (DOM) is a programming interface for HTML. It represents the page so that programs can change
    the document structure, style, and content. The DOM represents the document as nodes and objects.
    That way, programming languages can connect to the page. The DOM is an object-oriented representation of the web page,
    which can be modified with a scripting language such as JavaScript.
    
67 What are events and how/why to use them in Javascript?
    JavaScript's interaction with HTML is handled through events that occur when the user or the browser manipulates a page.
	element.addEventListener('event', 'function')
	
68 What is event bubbling/capturing? How would you use it?
    When an event happens on an element, it first runs the handlers on it, then on its parent, then all the way up on other ancestors.
    The process is called 	“bubbling”, because events “bubble” from the inner element up through parents like a bubble in the water.
		event.target
		A handler on a parent element can always get the details about where it actually happened. 
		    The most deeply nested element that caused the event is called a target element, accessible as event.target.
			event.target – is the “target” element that initiated the event, it doesn’t change through the bubbling process.
			this – is the “current” element, the one that has a currently running handler on it.
		
69 What is JSON and how do we use it?
    JSON is a string format which is very similar to the one that javascript uses to define objects.
    Browsers has a built in JSON object to convert a variable to JSON string (JSON.stringify function)
    and to convert a JSON string back to a variable (JSON.parse function).


## Software engineering

### Version control

70 What type of branching strategy would you use?
    Git flow:
		Master Branch
			Develop branch
				Feature Branch 1
				Feature Branch 2
	Merge feature branches into develop.
	If develop works, and final, merge it into Master.
	
71 What would you do if you find a bug on the production code (master branch)?
    Opeen a hotfix branch directly from master.
	When ready, merge hotfix branch back to Master.
	
72 How can you move changes from one branch to another in GIT?
    GIT merge

73 How does a VCS help with code reviews?
    With pull requests, merge will only happen if an authorized person approves the request.
    
74 What is your favorite git command? Why?
    GIT merge - indicates that a feature is ready (or we think its ready). + there is the buzz wether we get a merge conflict
    
75 What does remote/local mean in Git? 
    local: local machine - only accessible by the workstation
	remote: remote deposit (server) - accessible by all participating developers
	

### DevOps

76 Why is it good to use a package manager software?
    A package is an archive that contains binaries of software, configuration files, and information about dependencies.	
	Python – Managers: pip / conda
	Package Managers are used to automate the process of installing, upgrading, configuring, and removing programs.
	Also, they manage dependencies to ensure a package is installed with all packages it requires, thus avoiding dependency hell.

77 Why is it good to use a virtual environment for a project?
    A virtual environment basically a collection of softwares with fixed versions. The development of a product is done within this fixed environment.
    It is important because functions may behave/run differently among different softvare versions.
    If we change the environment, the very same code that worked before may not behave the same way in the new environment.
    It is essential that all developers use the same virtual environment suring the project. USE "requirements.txt" for storing the VE conditions.


### Networks

78 What kind of HTTP status codes do you know?
    1xx: Informational response
	2xx: Success
	3xx: Redirection
	4xx: Client error
	5xx: Server error
	Example:
		HTTP Status Code - 200 OK
		The request has succeeded. The information returned with the response is dependent on the method used in the request.
		HTTP Status Code - 300 Multiple Choices
		The requested resource has different choices and cannot be resolved into one. For example, there may be several index.html
		   pages depending on which language is wanted 
		HTTP Status Code - 404 Not Found
		The server has not found anything matching the Request-URI. No indication is given of whether the condition is temporary or permanent.
		HTTP Status Code - 500 Internal Server Error
		The server encountered an unexpected condition which prevented it from fulfilling the request.
		
79 What is a API?
    API is the acronym for Application Programming Interface, which is a software intermediary that allows two applications to talk to each other.
    Modern APIs adhere to standards (typically HTTP and REST), that are developer-friendly, easily accessible and understood broadly.
	AJAX:
	In simple terms, AJAX (Asynchronous Javascript and XML) is a technique that allows web pages to be updated
	asynchronously through the exchange of little amounts of data between clients and the servers in the background.
	AJAX combines JavaScript and XML (or JSON) making it possible to update parts of a webpage, without reloading the whole page.
	It allows clients to make asynchronous calls. By allowing asynchronous calls, AJAX saves time for the client browser
	by enabling it to display parts of information on a specific page instead of waiting for all data to arrive to allow the users to can act once more.
	Increased performance speed. By allowing sending and retrieval of information to and from the server without the full-page data,
	AJAX improves the speed, performance, and usability of web applications.
	We can fetch data from our local machine or server, public API.

80 What is REST API?
    REST, or REpresentational State Transfer, is an architectural style for providing standards between computer systems on the web,
    making it easier for systems to communicate with each other. REST-compliant systems, often called RESTful systems.
	SEPARATION OF CLIENT AND SERVER: the code on the client side can be changed at any time
	without affecting the operation of the server, and vica-versa.
	STATELESSNESS: the server does not need to know anything about what state the client is in and vice versa.
	In this way, both the server and the client can understand any message received, even without seeing previous messages.
	COMMUNICATION BETWEEN CLIENT AND SERVER: in the REST architecture, clients send requests to retrieve or modify resources,
	and servers send responses to these requests. There are 4 basic HTTP verbs we use in requests to interact with resources in a REST system:
		GET — retrieve a specific resource (by id) or a collection of resources
		POST — create a new resource
		PUT — update a specific resource (by id)
		DELETE — remove a specific resource by id
	
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
