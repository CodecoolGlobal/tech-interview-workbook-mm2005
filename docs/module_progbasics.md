# Programming Basics questions

## Computer science

### Data structures

1 What is the purpose of a list (array in some programming languages) data structure? Name some methods of it!
    Srote a collection of data in one variable, datas can be several types like integer, string, lists. You can reach element by index, and it's also mutable. methods: append, extrend, pop, insert, short, reverse. Reach element by index.

2 What is the difference between a list/array and a set?
    Set is unindexed, unordered and you can not change items (inmutable). Because it just stores the data random, you can't store the same element more times.

3 What is the purpose and methods of a dictionary/map data structure?
    In dictionaries key:value pairs are stored. Keys must be inmutable and must be unique, while values are allowed to be any data type and can be repeated. You can reach element by key. Methods: get, pop, update, copy, clear, remove. 

### Algorithms

4 Fibonacci sequences. Write a method (or pseudo code), that generates the Fibonacci sequences.
    def fibonacci (num_of_element):
        fibonacci_numbes = [0,1]
        for numbers in range(num_of_element-2):
            fibonacci_numbes.append(fibonacci_numbes[numbers]+fibonacci_numbes[numbers+1])
        retur fibonacci_numbes

5 How do you find a max value in a list/array if you can’t use any built-in functions?
    def max_element (list_of_numbers):
        max_value = list_of_numbers[0]
        for number in list_of_numbers:
            if number >= max_value:
                max_value = number
        return max_value

6 How do you find the average of values in a list/array if you can’t use any built-in functions?
    def avg (list_of_numbers):
        sum_of_numbers = 0
        for number in list_of_numbers:
            sum_of_numbers += number
        return avarage = sum_of_numbers/len(list_of_numbers)

7 What do we call an *in-place* sort?
    The sort() method, which modifies the original list, instead of creating another one like sorted().

8 Explain an algorithm which sorts a list!
    This simple sorting algorithm iterates over a list, comparing elements in pairs and swapping them until the larger elements "bubble up" to the end of the list, and the smaller elements stay at the "bottom".

### Programming paradigms - procedural

9 What is the call stack?
    Call stack is a stack data structure that stores information about the active subroutines of a computer program.

10 What is “Stack overflow”?
    When the stack is too long. Stack overflow occurs. Stack overflow is an error, which usually causes the program to crash.

11 What are the main parts of a function?
    def    name   ()    between "()" some input parameter   :    
        indentation    body

### Programming languages - Python  
12 How do you use a dictionary in Python?
    dic = { key1 : value1, key2 : value2} like in real life, unique keys and you can reach the values by it's key

13 What does it mean that an object is immutable in Python?
    You can not modify it after the creation. (mean, if you change it, you will changhe the memori adress too, so the original data doesn't changed)

14 What is conditional expression in Python?
    if, elif, else

15 What are different types of arguments in Python?
    Default argument (statement = True), keyword argument (statement), Arbitary argument (*statement)

16 What is variable shadowing? (context: variable scope)
    Variable shadowing is when a variable in a certain scope has the same name as another variable outside that scope. So the local overwrite the global (or even built-in)

17 What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?
    index error

18 What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?
    Local(L): Defined inside function/class
    Enclosed(E): Defined inside enclosing functions(Nested function concept)
    Global(G): Defined at the uppermost level
    Built-in(B): Reserved names in Python builtin modules

19 If you need to access the iterator variable after a for loop, how would you do it in Python?
    create a list and append it in the loop

20 What type of elements can a list contain in Python?
    Any (int,float,str,bol)

21 What is slice operator in Python and how to use?
    slice elements  slice(start,stop,step)

22 What arithmetic operators (+,*,-,/) can be used on lists in Python? What do they do?
    +,*

23 What is the purpose of the in and not in membership operators in Python?
    to tell is something in (or not in) a list, or string

24 What does the + operator mean when used with strings in Python?
    add the second to the end of the first

25 Explain f strings in Python?
    formated string (to put variables into the sring)

26 Name 4 iterable types in Python!
    list, dict, string, set

27 What is the difference between list/set/dictionary comprehension and a generator expression in Python?
    In list=set/dict/ comprehension square brackets are used, while a generator expression is surrounded by round parentheses. A generator expression is more memory efficient, since while list comprehension produces an entire list, generator expression produces one item at a time.

28 Does the order of the function definitions matter in Python? Why?
    No, because it just run when we call it.

29 What does unpacking mean in Python?
     Unpacking is used when we want to use for e.g. a list (or other types of data sturcture) containing the parameters of a function. In this case we cannot simply pass the list to the function, we have to unpack the list by including a * sign, like that: function(*list).

30 What happens when you try to assign the result of a function which has no return statement to a variable in Python?
    got None

## Software engineering

### Debugging

31 What techniques can you use while debugging a program in Python?
    rubber duck, print/trace debugging, debugger

32 What does step over, step into and step out mean while using the debugger?
    step over,into,out of a functoin

33 How can you start to debug a program from a certain line using the debugger?
    put the breakepoint to there

### Version control

34 What are the advantages of using a version control system?
    you know who did what and when (you can follow the lifetime of the prog) and backup

35 What is the difference between the working directory, the staging area and the repository in git?
    Working directory: where you are currently working, it is an untracked area of git, 'git add' puts the files to the staging area. Staging area: where git starts to track the changes in the files, 'git commit' puts the files to the repository. Git repository: where all the files are saved from your git directory.

36 What are remote repositories in git?
    Remote repositories are used to store files in a server that is accessible to multiple people working on the same project, instead of a local repository, which is only accessible by one person. For e.g.: Github repositories.

37 Why does a merge conflict occur?
    Merge conflict occurs when two commits made changes on the same object/function and git cannot decide which to implement in the merge.

38 Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
    git add -- git commit -- git push

39 What does it mean atomic commits and descriptive commit messages?
    atomic is meaning often commit after every small changes, descriptive means that the commit is a short descriptive commit about the changes (atomic: often, descriptive: how short,understable)

40 What’s the difference between git and GitHub?
    git is the version control system, github is a cloud hosting system

## Software design

### Clean code

41 What does clean code mean?
    Clean code is code that is easy to understand and easy to change.

42 What steps do we usually do during a clean code refactoring?
    Read through the whole code Summarize what is the purpose of the script in one sentence. Run the code to see what is the end result The code should keep runnable and show the same content when you finish the refactor Remove clutter Format your code Delete comments Remove complexity improper variable scopes Remove cleverness Remove the 3 D's

### Error handling

43 What is exception handling?
    When the program can't do something, and stops you can handle that situation.

44 What are the basics of exception handling in Python?
    try, except.

45 In which case should we catch an exception? Why?
    if the try can't run 

46 What can/should we do with an exception in the ‘except’ block?
    Anything (should print error message)

47 What does the else and finally statement do in a try-except block in Python?
    Else runs if try runed
    Finally always runs after try/except

## Software Development Methodologies

48 What is the main goal of a retrospective meeting?
   The goal of retrospectives is helping teams to improve their working culture.

## Programming environment

### Unix

49 What is UNIX and what is Linux?
    Unix is a is a multiuser and multitasking computer operating system. Nowadays UNIX is more like a trademark wich means the family of operating systems.
    Linux is an open source operating system. Today there are a lots of versions of Linux and we call them distributions.   

50 What do we call the shell in Linux?
     The shell is the command interpretor in an operating system such as Linux, it is a program that executes other programs. It provides a computer user an interface to the system so the user can run different commands or utilities/tools with some input data.

51 What does root means in a Linux environment?
    Root is the user name or account that by default has access to all commands and files in the operating system. 

52 How do you access your personal files in Linux?
    from home directory

53 How can you install an application in Linux?
    In the terminal use "sudo apt install + application name" command.

54 What is package management in Linux, what are repositories?
    PM is for softwer intalling or maintaning, repos are servers that contains the pcakages


55 How do you navigate in the filesystem with the command line?
    There are some commands:
        cd - change directory ("cd + directory name" takes to the "directory name" directors)
        cd .. - navigate one directory level up 
        pwd - print the working directory
        ls - print the items in the working directory
    
56 What does the following commands do: mkdir, rm, cat, cp, touch?
    mkdir command create new directories if they do not already exist on the file systems
    rm delete file
    cat print the file with the standard output
    cp copy the file with a new filename
    touch make a new file (empty)

57 How can you look up what does a command do in Linux if you have no internet connection?
    Use the help command (like "cd --help")

58 What does the following commands do: head, tail, more, less?
    head/tail print the first/last 10 lines of the file
    more displays the file in a scrollabe mose
    less display one schreen file content in a time.

59 How do you download a file from internet using the terminal?
    With the comman "wget + URL" with a new name  "wget -o  filename URL"