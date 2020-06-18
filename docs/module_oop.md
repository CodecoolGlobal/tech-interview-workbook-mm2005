# OOP questions

## Software design

### Error handling

1 What does 'fail fast' mean in terms of exception handling? Why is it a good practice?

    If an error occurs, the software should fail immediately and visibly. If something unusually or unexpectedly occurs,
     let the software fail immediately instead of postponing the failure or working around the failure.
    
    It's a good practice because:
    -   Bugs can be detected earlier, and they're easier to reproduce and faster to fix. 
    -   It’s faster to stabilize softwares.
    -   Fewer bugs and defects will go into production, thus leading to higher-quality and more production-ready software.
    -   The cost of failures and bugs are reduced.
## Computer Science

### Data structures

2 How to find the middle element of singly linked list in O(n)?

    -   Even number of elements: return list.get(n / 2)
    -   Odd number of elements: return list.get(n / 2 + 1)

3 Given an array of integers going from 1 to 100 (both inclusive) there is a duplicated entry. How to find it?

    Get a sum of the array's values and cast the array to a set. Get a sum of the set's values too,
    this way the difference between the two sums will be the duplicated value.
    
4 What is a linked list? How to find if a linked list has a loop?

    A linked list is a linear collection of data elements, whose order is not given by their place in memory.
    Instead, each element points to the next. In a doubly linked list an element points to the previous too.
    
    You can find out if it has a loop while iterating through the list and keep putting the node addresses in a Hash Table.
    At any point, if NULL is reached then return false
    and if next of current node points to any of the previously stored nodes in Hash then return true.

5 What is the Big O time complexity of the common operations in an ArrayList, LinkedList, HashMap?
And of a bubble sort, quicksort, finding items in a Binary Search tree?

    | Time | Add | Remove | Get | Contains |
    |:-----|:---:|:------:|:---:|:--------:|
    | ArrayList | O(n) | O(n) | O(1) | O(n) |
    | LinkedList | O(1) | O(1) | O(n) | O(n) |
    | HashMap | O(1) | O(1) | - | O(1) |
    
    Bubble sort: O(n2) - Bubble Sort compares all the element one by one and sort them (swap them) based on their values.
    
    Quicksort: O(log 2n) - It works by selecting a 'pivot' element from the array and partitioning the other elements
    into two sub-arrays, according to whether they are less than or greater than the pivot. The sub-arrays are then sorted recursively. 
    
    Finding items in a Binary Search tree: O(n) if all elements on the same side. O(log n) if the tree is balanced.

6 How does HashMap work?

    On principle of Hashing. (Two equal objects must produce the same hash code consistently.)
    Every map is an object that maps keys to values. It uses an array and LinkedList data structure internally for storing Key and Value.

7 Why is it important for keys in a map to have an immutable type? (Consider String for example.)

    If immutable, the object's hashcode won't change, and it allows caching the hashcode of different keys
    which makes the overall retrieval process very fast. Also, for mutable objects ,the hashCode() might be dependent on
    fields that could change, if this happens you won't be able to find the key (and its value) in the HashMap
    since hashCode() returns different value.


### Other

8 What is a garbage collector, in a nutshell?

    In computer science, garbage collection (GC) is a form of automatic memory management.
    The garbage collector, or just collector, attempts to reclaim garbage, or memory occupied by objects
    that are no longer in use by the program. Garbage collection was invented by John McCarthy around 1959
    to simplify manual memory management in Lisp.
    
    A garbage collector's main objective is to free heap memory by destroying unreachable objects.
    There are generally four different ways to make an object eligible for garbage collection.
    -   Nullifying the reference variable
    -   Re-assigning the reference variable
    -   Object created inside method
    -   Island of Isolation


## Programming paradigms

### Procedural

9 What is casting? What is the difference between up vs downcasting?

    Casting is taking an Object of one particular type and "turning it into" another Object type.
    Downcasting is when you take an object and cast it to a more "specific" type of Object.
    Upcasting is when you take an object and cast is to a more "generic" type of Object. e.g. Downcasting:
    `
    Object object = "sample";
    String string = (String) object;
    `
    
10 Which order should we catch the exceptions? Why?

    The most specific should be the first exception, and the most generic should be the last one.
    This way specific exceptions won't be omitted occasionally by more general catch blocks.

### Object-oriented

11 What is a class?

    A class is the blueprint from which individual objects are created.
    
12 What is an object?

    An object is a software bundle of variables and related methods.
    
13 What is a constructor?

    Constructor is a block of code that initializes the newly created object.
    A constructor resembles an instance method in java but it’s not a method as it doesn’t have a return type.
    
14 Do we require parameter for constructors?

    There are three types of constructors:
    -   Default (No constructor implemented)
    -   No-arg
    -   Parameterized
    Only parameterized constructors needs parameters. E.g:
    `java
    public class Person {
        int age;
        String name;
    
        Person(int age, String name){
            this.age = age;
            this.name = name;
        }
    }
    `

15 What is an interface?

    In its most common form, an interface is a group of related methods with empty bodies.
    Implementing an interface allows a class to become more formal about the behavior it promises to provide.
    Interfaces form a contract between the class and the outside world, and this contract is enforced at build time by the compiler.
    If your class claims to implement an interface, all methods defined by that interface must appear in its source code
    before the class will successfully compile.

16 What are access modifiers?

    A Java access modifier specifies which classes can access a given class and its fields, constructors and methods.
    Access modifiers can be specified separately for a class, its constructors, fields and methods. There are four of them:
    -   private (visible from inside the same class)
    -   default (visible from inside the same package)
    -   protected (visible from subclasses of the superclass even outside the package)
    -   public

17 What is data hiding?

    Encapsulation is a central design principle of OOP.
    It means that the internal structure, and the implementation of a class should be hidden from the world.
    This can be done by restricting the access to these parts.

18 Can a static method use non-static members?

    A static method can access non-static methods and fields of any instance it knows of.
    However, it cannot access anything non-static if it doesn't know which instance to operate on.

19 What is the difference between hiding a static method and overriding an instance method?

    Overriding basically supports late binding. Therefore, it's decided at run time which method will be called. It is for non-static methods.
    
    Hiding is for all other members (static methods, instance members, static members).
    It is based on the early binding. So, the method or member to be called or used is decided during compile time.

20 Define the following terms: Instantiation, Attribute, Method

    The phrase "instantiating a class" means the same thing as "creating an object."
    When you create an object, you are creating an "instance" of a class, therefore "instantiating" a class.
    The new operator instantiates a class by allocating memory for a new object and returning a reference to that memory.
    The new operator also invokes the object constructor.
    
    An attribute is another term for a field. It's a variable for a class.
    
    A method is a block of code which only runs when it is called. You can pass data, known as parameters, into a method.
    Methods are used to perform certain actions, and they are also known as functions.

21 Could we access a static variable (or method) from a non-static method? Why?

    Yes, a non-static method can access a static variable or call a static method in Java.
    There is no problem with that because of static members i.e. both static variable and static methods belongs to a class
    and can be called from anywhere, depending upon their access modifier.
    For example, if a static variable is private then it can only be accessed from the class itself,
    but you can access a public static variable from anywhere.
    Similarly, a private static method can be called from a non-static method of the same class, but a public static method e.g. main()
    can be called from anywhere.

22 Could we access a non-static variable (or method) from a static method? Why?

    You cannot access a non-static variable from a static method without an instance, because they don’t exist without their instance.
    
23 How many instances you have of a static variable of a given class?

    Only one copy of the static variable exists regardless of the number of instances of the class.
    When you declare a field in a class in Java as static and set it to a value, every instance object of that class refer to the same value.
    If you change the value, all instances will see that change.

24 Why is it not a good practice to write a lot of static methods?

    Interfaces and abstract classes only define non-static methods.
    Static methods thus don't fit very well into inheritance.
    Note also that static methods do not have access to "super", which means that static methods cannot be overridden in any real sense.
    Actually, they can't be overridden at all, only hidden.

25 What are the features of static attributes and static methods of a class? What are the benefits, when to use them?

    Static methods and fields are useful when they conceptually don't belong to an instance of something.
    Consider a Math class that contains some common values like Pi or e, and some useful functions like sin and cos.
    It really does not make sense to create separate instances to use this kind of functionality, thus they are better as statics:
    `
    // This makes little sense
    Math m = new Math();
    float answer = m.sin(45);
    
    // This would make more sense
    float answer = Math.sin(45);
    `
    
26 What is the ‘this’ reference?

    ‘this’ is a reference variable that refers to the current object. There are 6 ways to use 'this':
    -   To refer current class instance variables.
    -   To invoke current class constructor.
    -   To return the current class instance.
    -   As a method parameter.
    -   To invoke current class method.
    -   As an argument in the constructor call.


27 What are base class, subclass and superclass?

    In an OOP language, the base class is a class from which other classes are derived from.
    
    The top-most "base" class, the class from which all other classes are derived, is the Object class defined in java.lang.
    Object is the root/base of a hierarchy of classes but in many illustrations you will see the Object class shown above of all classes at the top.
    
    Generally the class that is derived from another class is called a subclass.
    The class from which it's derived is called the superclass. So the subclass is "under" the superclass.
    So the father of all superclasses is the Object class.

28 Draw an object oriented family (as entities, with relations) on the whiteboard.


29 Difference between overloading and overriding?

    | Overloading |
    Method overloading is used to increase the readability of the program.
    Method overloading is performed within class.
    In case of method overloading, parameter must be different.
    Method overloading is the example of compile time polymorphism.
    In java, method overloading can't be performed by changing return type of the method only.
    Return type can be same or different in method overloading. But you must have to change the parameter.	
 
    | Overriding |
    Method overriding is used to provide the specific implementation of the method that is already provided by its super class. 
    Method overriding occurs in two classes that have IS-A (inheritance) relationship.
    In case of method overriding, parameter must be same. 
    Method overriding is the example of run time polymorphism.
    Return type must be same or covariant in method overriding. 

30 What are the Object Oriented Principles? Explain the concepts with realistic examples!

    There are 4 major principles that make an language Object Oriented. 
    -   Encapsulation
        -   Encapsulation is the mechanism of hiding of data implementation by restricting access to public methods.
            Instance variables are kept private and accessor methods are made public to achieve this.
    -   Abstraction
        -   Abstract means a concept, or an idea which is not associated with any particular instance.
            Using abstract class/Interface we express the intent of the class rather than the actual implementation.
            In a way, one class should not know the inner details of another in order to use it, just knowing the interfaces should be good enough.
    -   Inheritance
        -   Inheritances express “is-a” and/or “has-a” relationship between two objects.
            Using Inheritance, In derived classes we can reuse the code of existing super classes.
            In Java, concept of “is-a” is based on class inheritance (using extends) or interface implementation (using implements). 
    -   Polymorphism
        -   It means one name many forms. It is further of two types — static and dynamic.
            Static polymorphism is achieved using method overloading and dynamic polymorphism using method overriding.
            It is closely related to inheritance. We can write a code that works on the superclass, and it will work with any subclass type as well.

31 What is method overloading?

    Method Overloading is a feature that allows a class to have more than one method having the same name, if their argument lists are different.
    It is similar to constructor overloading in Java, that allows a class to have more than one constructor having different argument lists.

32 What is method overriding?

    Declaring a method in sub class which is already present in parent class is known as method overriding.
    Overriding is done so that a child class can give its own implementation to a method which is already provided by the parent class.
    In this case the method in parent class is called overridden method, and the method in child class is called overriding method.

33 Explain how object oriented languages attempt to simplify memory management for Programmers.

    OOP Languages usually have a Garbage Collector (GC) which's purpose is to deallocate objects when they can't be reached anymore.
    It happens when there's no more references to them. This way the programmer doesn't have to perform memory management manually.

34 Explain the “Single Responsibility” principle!

    It means that a class/module should only be responsible for a single task.
    That's why when we want to change it, we must only have one reason for it.

35 What is an object oriented program? Explain, show.

    OOP is a programming paradigm based on the concept of "objects", which can contain data, in the form of fields,
    and code, in the form of procedures. A feature of objects is an object's procedures
    that can access and/or modify the data fields of the object with which they are associated with.

36 How do you make a class immutable? What do you need to watch out for?

    `java
    public final class Person{
        final int age;
        final String name;
        
        public Person(int age, String name){
            this.age = age;
            this.name = name;
        }
        
        public int getAge(){
            return this.age;    
        }   
        
        public String getName(){
            return this.name;
        }
    }
        `
    Following are the requirements:
    -   The class must be declared as final (So that child classes can’t be created).
    -   Data members in the class must be declared as final (So that we can’t change the value of it after object creation).
    -   A parameterized constructor.
    -   Getter method for all the variables in it.
    -   No setters(To not have the option to change the value of the instance variable).
    
37 How many instances can be created for an abstract class?

    It is not possible to create an abstract class because you do not have all the right implementations to make it happen.
    The abstract class serves another purpose which is to make sure that you have a base for all of your subclasses.
    This means that on its own, this is basically empty and unusable. You can use it in order to improve it or build on it.

## Programming languages

### Java

38 What is autoboxing and unboxing?

    Autoboxing is the automatic conversion that the Java compiler makes between the primitive types, and their corresponding object wrapper classes.
    For example, converting an int to an Integer, a double to a Double, and so on. If the conversion goes the other way, this is called unboxing.

39 If you have a variable, that shall store a positive whole number between 0 and 200, what primitive type would you use to store it?
    
    The most efficient would be to store it in byte, but that would harden the readability.
    A byte can store values from -128 to 127 this way every number should be extracted by 128. The more sophisticated (lifelike) version is to store it in a short.

40 What is the "golden rule" of variable scoping in Java? What is the lifetime of variables?

    The golden rule is that static code cannot access non-static members by their simple names.
    Static code is not executed in the context of an object, therefore the references this and super are not available.
    An object has knowledge of its class, therefore, static members are always accessible in a non-static context. Lifetime of variables:
    
    | Type | Description | 
    
    | Instance variables | The lifetime of an instance variable is until the object stays in memory. |
    | Class variables | The general scope of a class variable is throughout the class and the lifetime of a class variable
                        is until the end of the program or as long as the class is loaded in memory. |
    | Local variables | Scope of a local variable is within the block in which it is declared and the lifetime of a local variable
                        is until the control leaves the block in which it is declared. |

41 What is the purpose of the ‘equals()’ method?

    Its purpose is to check whether two objects contains the same data or not.  

42 What is the difference between '==' and 'equals()'?

    The "==" operator, returns true only if the two objects are the same (even has the same memory address), not only their value is the same.

43 What does the ‘static’ keyword mean?

    It means that only one instance of a static field exists even if you create a million instances of the class, or you don't create any. It will be shared by all instances.

44 Why is the main() method declared as static? Explain.

    Because they can then be invoked by the runtime engine without having to instantiate any objects then the code in the body of main() will do the rest.

45 What is the default access modifier in a class?

    When no access modifier is specified for a class , method or data member – It is said to be having the default access modifier by default.
    The data members, class or methods which are not declared using any access modifiers i.e. having default access modifier are accessible only within the same package.

46 What is the JVM?

    The Java Virtual Machine manages system memory and provides a portable execution environment for Java-based applications.
    The JVM has two primary functions: to allow Java programs to run on any device or operating system, and to manage and optimize program memory.

47 What is the difference between the JRE and the JDK?

    The JRE is the Java Runtime Environment. It is a package of everything necessary to run a compiled Java program, including the Java Virtual Machine (JVM),
                                             the Java Class Library, the java command, and other infrastructure. However, it cannot be used to create new programs.
    
    The JDK is the Java Development Kit, the full-featured SDK for Java. It has everything the JRE has, but also the compiler (javac) and tools (like javadoc and jdb).
                                         It is capable of creating and compiling programs.

48 What is the difference between long and Long?

    -   The long is primitive type, while Long is the object from long.
    -   The long is passed by value and Long is passed by reference.
    -   You can initialize Long to null.
    Rule of thumb - always prefer primitive types unless you need it in object form.

49 Can a long store bigger numbers than a Long?

    Since Long is only the wrapper class for long, and doesn't limit it's range they can store equally big numbers.

50 What kind of packages do you know under java.util.* ? Bring at least 3 examples.

    -   Date
    -   List
    -   Set
    -   Random
    -   Currency

51 What are the access modifiers in Java? Which one could we use for class?

    A Java access modifier specifies which classes can access a given class and its fields, constructors and methods.
    Access modifiers can be specified separately for a class, its constructors, fields and methods. There are four of them:
    -   private (visible from inside the same class)
    -   default (visible from inside the same package)
    -   protected (visible from subclasses of the superclass even outside the package)
    -   public
    Classes can only have the default (package) and public access modifier assigned to them.

52 Can an “enum” contain methods in Java? Explain.

    Yes it can, You call a Java enum method via a reference to one of the constant values.

53 When would you use a private/protected/public attribute? What is the difference?

    Private Access modifier: This modifier is open to use within the class that defines it. ( it can’t be accessed outside the class means in inherited class).
    
    Protected Access modifier: This modifier is open to use within the class in which it is defined and its parent or inherited classes.
    
    Public Access modifier: This modifier is open to use inside as well as outside the class.

54 How do you prevent developers from subclassing a class?

    While one of Java's strengths is the concept of inheritance, in which a class can derive from another,
    sometimes it's desirable to prevent inheritance by another class. To prevent inheritance, use the keyword "final" when creating the class.

55 How do you prevent developers from overriding a method in a subclass?

    Apart from final methods there are two more techniques which you can use to prevent a method from being overridden in Java.
    Private method is not accessible in subclass, which means they can not be overridden as well, because overriding happens at child class.
    Similarly, static methods can not be overridden in Java, because they are resolved and bonded during compile time, while overriding takes place at runtime.
    They are resolved based upon the type and not object.

56 How do you prevent developers from changing the value of a variable?

    If you would like to prevent the value of variable which is of primitive type, you can do so using final keyword.

57 Think about money ;) How would you store a currency value, that shall support decimal parts? Think it through again, and try to think outside of the box!
58 What happens if you try to call something, that you have no access to, because of data hiding?
59 What happens if you try to delete/drop an item from an array, while you are iterating over it?
60 What happens if you try to delete/drop/add an item from a List, while you are iterating over it?
61 What happens if you try to add an item to the end of an array, while you are iterating over it?
62 If you need to access the iterator variable after a for loop, how would you do it?
63 Which interfaces extend the Collection interface in Java. Which classes?
64 What is the connection between equals() and hashCode()? How are they used in HashMap?
65 What is the difference between checked exceptions and unchecked exceptions? Could you bring example for each?
66 What is Error in Java and how does it relate to Exception?
67 When does 'finally' block run? What it is used for? Could you give an example from your projects when you would use 'finally'?
68 What is the largest number you can work with in Java?
69 When you use method overriding, can you change the access level of the method, from protected to public? Why?When you use method overriding, can you change the access level of the method, from public to protected? Why?
70 Can the main method be overridden? Explain your answer!
71 When you use method overriding, can you throw fewer exceptions in the subclass than in the parent class? Why?
72 When you use method overriding, can you throw more exceptions in the subclass than in the parent class? Why?
73 What does "final" mean in case of a variable, method or a class?
74 What is the super keyword?
75 What are “generics”? When to use? Show examples.
76 What is the benefit of having “generic” containers?
77 Given two Java programs on two different machines. How can you communicate between the two? What are the possible ways?
78 What is an annotation? What can be annotated and how? Show examples.

### C&#35;

#### Explain the purpose of IL and how does it relate to CLR?
#### What does “managed code” mean?
#### What is an assembly?
#### What is the difference between an EXE and a DLL?
#### What is strong-typing versus weak-typing? Which is preferred? Why?
#### What is a namespace?
#### Explain sealed class in C#?
#### What is explicit vs. implicit conversion? Give examples of both of them.
#### Is a struct stored on the heap or stack?
#### Can a struct have methods?
#### Can DateTimes be null?
#### List out the differences between Array and ArrayList in C#?
#### How is the using() pattern useful? What is IDisposable? How does it support deterministic finalization?
#### How can you make sure that objects using dedicated resources (database connection, files, hardware, OS handle, etc.) are released as early as possible?
#### Why to use keyword “const” in C#? Give an example.
#### What is the difference between “const” and “readonly” variables in C#?
#### What is a property in C#?
#### List out two different types of errors in C#?
#### What is the difference between “out” and “ref” parameters in C#?
#### Can we override private virtual method in C#?
#### What's the difference between IEquatable and just overriding Object.Equals()?
#### Explain the differences between public, protected, private and internal. Explain access modifier – “protected internal” in C#!
#### What’s the difference between using `override` and `new` keywords when defining method in child class?
#### Explain StringBuilder class in C#!
#### How we can sort the array elements in descending order in C#?
#### Can you use a value type as a generic type argument in C#? For example when implementing an interface like (IEquatable).
#### What are Nullable Types in C#?
#### Conceptually, what is the difference between early-binding and late-binding?
#### What is delegate, event, callback, multicast delegate?
#### What is enum in C#?
#### What is null-conditional operator?
#### What is null-coalescing operator?
#### What is serialization?
#### What is the difference between Finalize() and Dispose() methods?
#### How do you inherit a class from another class in C#?
#### What is difference between “is” and “as” operators in C#?
#### What are indexers in C# .NET?
#### What is the difference between returning IQueryable<T> vs. IEnumerable<T>?
#### What is LINQ? Explain the idea of extension methods.
#### What are the advantages and disadvantages of lazy loading?
#### How to use of “yield” keyword? Mention at least one practical scenario where it can be used?
#### What are attributes in C#? Give some examples of usage of them.
#### By what mechanism does NUnit know what methods to test?
#### What is the GAC? What problem does it solve?
#### What is the largest number you can work with in C#?

### Database

79 How can you connect your application to a database server? What are the possible ways?

    Java can reach the database via two different interfaces:
    -   JDBC (Java DB Connectivity) is the lower level. You can run SQL queries via this.
    -   JPA (Java persistence API) is the higher level one. This is the Java standard for ORM ( Object Relational Mapping). 
    I. e. it maps DB tables to classes so the Java developer do not need to deal with DB tables, only objects.
    
    There are 5 steps to connect any java application with the database using JDBC. These steps are as follows:
    -   Register the Driver class
        `
        public static void forName(String className) throws ClassNotFoundException{
            Class.forName("oracle.jdbc.driver.OracleDriver);
        }
        `
    -   Create connection
        `
        public static Connection getConnection(String url) throws SQLException{
            Connection con=DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe","system","password");  
        }
        `
    -   Create statement
        `
        public Statement createStatement()throws SQLException{
            Statement stmt=con.createStatement();  
        }
        `
    -   Execute queries
        `
        public ResultSet executeQuery(String sql)throws SQLException{
            ResultSet rs=stmt.executeQuery("select * from emp");
            while(rs.next()){
                System.out.println(rs.getInt(1)+" "+rs.getString(2));  
            }
        }
        `
    -   Close connection
        `
        public void close()throws SQLException{
            con.close();
        }
        `

80 What do you know about database normalization?

    Normalization is the process of efficiently organizing data in the database.
    It's goal is to eliminate redundant data & ensure meaningful data dependencies. 
    1.  First Normal Form (1NF)
        - Create separate set of tables for each group of related data and identify each row with a unique columns [primary key]
          or set of columns [composite key]
        - Eliminate duplicate columns from the table
    2. Second Normal Form (2NF)
        - Meet all the requirements of the first normal form
        - Remove subsets of data that apply to multiple rows of a table and place them in separate tables
        - Create relationships between these new tables and their predecessors through the use of foreign keys
    3. Third Normal Form (3NF)
        - Meet all the requirements of the second normal form.
        - Remove columns that are not dependent upon the primary key.
    
    Advantages:
    -   Data can be stored as small atomic pieces
    -   Saves space
    -   Increases speed
    -   Reduces data anomalies
    -   Easy maintenance
