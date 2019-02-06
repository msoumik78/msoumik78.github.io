---
layout: post
title: "R fundamentals"
date: 2017-10-18 16:55:23 +0530
categories: "Data Science"
---

# R Fundamentals

R was invented by 2 persons in 1993 whose name start with R and hence the name of the language.
CRAN -- Comprehensive R Archive Network.
R programs can be written using R or R-Studio

R variable assignment can be done in either of the below ways (the first one is most commonly followed):
* x <- 3
* 3 -> x

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
* x <- 1:5
* x <- c(1, 2, 3,4,5)

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


### R Lists

In R - Lists are arrays which can contain elements of different data types, lists are created using syntax:
* x <- list(1, TRUE, c(1,2,3,4,5))

The indices can be named using the below command:
* names(x) <- c("one", "two", "three") 

Elements of the list can be accessed using ::
* y <- x[1]ory <- x$one
List elements can be extended as :
* x[5] <- "Soumik"
Lists can also be merged using :
* Z <- c(list1, list2)
Lists can be converted to vectors using the command: 
* z <- unlist(x)


Create a list containing a vector, a matrix and a list.
* list_data <- list(c("Jan","Feb","Mar"), matrix(c(3,9,5,1,-2,8), nrow = 2),   list("green",12.3))

Give names to the elements in the list:
* names(list_data) <- c("1st Quarter", "A_Matrix", "A Inner list")

Access the first element of the list:
* print(list_data[1])

Access the thrid element. As it is also a list, all its elements will be printed :
* print(list_data[3])


### R Matrix

Matrix is a 2 dimensional array and it can contain only elements of the same data type. Matrix can be created using the command:
* x <- matrix(c(1:6) , nrow=2, ncol=3, byRow = TRUE)

Output of the above is : 
1 2 3
4 5 6

rownames <- c("row1", "row2")
colnames <- c("col1", "col2", "col3")

x <- matrix(c(1:6) , nrow=2, ncol=3, byRow = TRUE, dimnames = list(rownames, colnames))

Since matrix is a 2 dimensional array which contains only elements of the same datatype - all arithmetic operations (+, -, *, /, %%, %/%) which are applicable to the vector are also applicable to the matrix.

