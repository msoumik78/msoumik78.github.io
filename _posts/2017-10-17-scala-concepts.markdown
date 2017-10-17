|layout|title|date|categories|
|---|---|---|---|
post|"Scala concepts"|2017-08-22 16:55:23 +0530|jekyll update| 

# Scala Concepts

### How to run a Scala Program

###### Scala import statements
* If everything is imported from a package – we use the underscore (_) in place of asterik. Like  - import x.y._
* Import statements can occur at any place of the source file (unlike java files where the import statement can only be at the top)
* With one import statement, 2 different classes (from the same package) can be imported. Like – import x.y{a,b}
* Import statements can also use aliasing, like – import scala.collection.mutable.{Map => MutableMap}
* Import everything from a package except a particular class - import scala.concurrent.{JavaConversions => _, _}.  This means import everything from scala.concurrent except JavaConversions.

###### How to package & run a Scala program
* There is no hard and fast rule that scala source file should contain a class name which is the same as the name of the source file.
* Normally in scala – the program is first compiled using  -scalac X.scalaand then run usingscala X
* However since this interpreter takes a while, there is another faster interpreter in scala termed as fsc. This one runs a server daemon process, hence the first time invocation can take a while but subsequent invocations are much faster.
* Scala has a command line REPL utility which can be used to run any command. Some commands can be put in a scala script file and then the file can be run using the command (however the script needs to have expression and not just class declaration):scala X.scala
* Semicolons at the end of each line of source code is not required.
* Multiline strings can be formed using triple quotes. 
Remember : This internally first compiles and then runs the bytecode

###### Some details about Scala classes & Objects

Some important aspects are as follows:
* Scala does not have the static keyword
* Instead of static keyword, scala has the concept of an object class – which is essentially a singleton object 
* Case classes are the simple immutable POJOs
    case class Person(firstName: String, lastName: String)
* Scala does not have operator and hence no operator overloading
* Normally parametrized classes are directly used and entire body of the class (minus method body) serves as the constructor.
For example the following class declaration in Scala:
    class Hello(name: String) {  
      // Statement executed as part of the constructor  
      println("New instance with name: " + name)   // Method which accesses the constructor argument  
      def sayHello = println("Hello, " + name + "!")}
The above code is equivalent to the below Java code :
    public class Hello {    
      private final String name;     
      public Hello(String name) {        
        System.out.println("New instance with name: " + name);        
        this.name = name;    
        }     
        public void sayHello() {        
          System.out.println("Hello, " + name + "!");    
         }
      }


###### Scala variable declarations

* Normally variable is declared using the keyword 'var' like– var x =  “My name is Soumik” . Scala has built in type inference and hence it can understand the variable type. Also one can declare variable using var x: String = “My name is Soumk”
* Variables can also be declared using the 'val' keyword, these variables can't be changed once assigned.

###### Scala Arrays, Lists, Tuple, Sets and Maps 

Arrays are mutable objects.
Lists are immutable and should contain element of same data type.
Tuples are also immutable but can contain elements of  different data types
A tuple is declared and accessed as below :
  val color = ("blue", 258, 'b') println(color._1)
  For each of Sets and Maps – there are 2 sets of packages (immutable and mutable). 
  
  Sets and Maps are declared as below:
    import scala.collection.mutable.HashMap
    val colorMap = new HashMap[Int, String] 
    colorMap += 1 -> "Blue" 
    colorMap += 2 -> "Red"
 A map can also be created using the syntax (basically → returns a tuple which is required to construct a map object) : 
 var a = Map(1 -> "Blue", 2 -> "Red", 3 -> "Green")Or
 var a = Map( (1, "Blue"), (2, "Red"), (3, "Green") )

###### Scala Methods

* Normally methods are declared using the def keyword.
* Methods may or may not contain return type and if it does not  then the last statement of the method is the value of the return statement.
* You can define a method within another method
* In scala, there are no operators – in fact the operators are the methods.
* Normal method declaration in scala is like below :
    def max(x: Int, y: Int): Int = if (x < y) y else x
* Since scala is a functional language, functions are first class objects and they can be passed as arguments to other functions like the below example:
    args.foreach(arg => println(arg))
* Functions can also be assigned to variables as below :
  var add = (x: Int, y: Int) => {  // More code  x + y }
 * Following is an example of a method where a function is passed as an argument to another function 
    object Timer {  def oncePerSecond(callback: () => Unit) 
      {    while (true) { callback(); Thread sleep 1000 }  }  
    def timeFlies() {    println("time flies like an arrow...")  }  
    def main(args: Array[String]) {    oncePerSecond(timeFlies)  }}
* Methods can have multiple parameter list like below :
    def add(x: Int)(y: Int) = x + y
// The method add2 has no parameter list; it fills in// only the first parameter list of the method add
    def add2 = add(2) _
// Call add2, which returns a function that takes one parameter,// then call that function with the argument 3
    val result = add2(3)
