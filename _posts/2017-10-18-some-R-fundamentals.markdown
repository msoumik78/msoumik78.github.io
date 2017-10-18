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

R index starts with 1.
Printing to the console can be done by using either print() or cat() commands
list of all variables set in the current session can be obtained as:ls (pattern ="", all.NAME ="TRUE")
  print(ls(pattern = "var"))   
A variable can be removed using the command:
  rm(x)
Also a couple of useful commands:  
  getwd() --> Gets the current working directory
  setwd() --> Sets the current working directory
  .libPaths() --> Prints the OS folder where the R packages are installed
  library() -> Prints the libraries which are already installed
  search() --> Checks the librarues which are already loaded in the current environment
  install.packages("") --> Installs the package directly from the CRAN
  install.packages("<Local folder location>" , repos="NUL", type="source") --> Installs the package manually from the zip file downloaded
  library("XML" , lib.loc="") --> Loads the specific library in the environment which has not been loaded by default
