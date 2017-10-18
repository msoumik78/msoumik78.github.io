|layout|title|date|categories|
|---|---|---|---|
|post|"R Concepts"|2017-10-18 10:30:00 +0530|jekyll update| 

# R Fundamentals

R was invented by 2 persons in 1993 whose name start with R and hence the name of the language.
CRAN -- Comprehensive R Archive Network.
R programs can be written using R or R-Studio

R variable assignment can be done in either of the below ways (the first one is most commonly followed):
x <- 3
3 -> x

Following are the major data types in R:
* Character
* Logical
* Integer
* Numeric
* Complex
* Raw / Binary

Some more R tips:
* R index starts with 1.
* Printing to the console can be done by using either print() or cat() commands
* list of all variables set in the current session can be obtained as:ls (pattern ="", all.NAME ="TRUE")
  print(ls(pattern = "var"))   
* A variable can be removed using the command:
  rm(x)
* Also a couple of useful commands:  
  * getwd() --> Gets the current working directory
  * setwd() --> Sets the current working directory
  * .libPaths() --> Prints the OS folder where the R packages are installed
  * library() -> Prints the libraries which are already installed
  * search() --> Checks the librarues which are already loaded in the current environment
  * install.packages("") --> Installs the package directly from the CRAN
  * install.packages("<Local folder location>" , repos="NUL", type="source") --> Installs the package manually from the zip file downloaded
  * library("XML" , lib.loc="") --> Loads the specific library in the environment which has not been loaded by default

### R String functions

Strings in R can be either in single or double quotes. Also a single quote can be within a double quote and vice versa.
* a <- 'Start and end with single quote'
* b <- "Start and end with double quotes"
* c <- "single quote ' in between double quotes"

{% highlight ruby %}

a <- "Hello"
b <- 'How'
c <- "are you? "
print(paste(a,b,c, sep = "-"))

{% endhighlight %}
Output: [1] "Hello-How-are you? "

Other important String functions include :
* toUpper()
* toLower()
* substring(X, 1, 5) --> Creates a string which occupies from the first to the fifth place
* result <- nchar("Count the number of characters")

print(result)Output: [1] 30

### R vectors

R index starts with 1
Vectors are arrays which can only contain elements of same data type. Ways to create vector are as follows :
x <- 1:5
x <- c(1, 2, 3,4,5)

Vector arithmethic can be done as :
{% highlight ruby %}
  x <- c(1,2,3,4,5)
  y <- c(1,2,3,4,5)
  z <- x + y
  print(z)
{% endhighlight %}
Output: [1] : ---------------2, 4, 6, 8 ,10---------------


{% highlight ruby %}
t <- c("Sun","Mon","Tue","Wed","Thurs","Fri","Sat")
u <- t[c(2,3,6)]
print(u)
{% endhighlight %}

Output : [1] "Mon" "Tue" "Fri"
