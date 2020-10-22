# Beginner R Programming for Anthropologists (and other folks too!)

Allison E. Mann, last updated May 21, 2018

### What is R and why should you use it?

* **R is freely available**
* Because R is open-source there are many packages that can be added for nearly any application (or you can write your own!)
* Publication ready, flexible graphics capabilities
* Supportive, active community of users
* Widely used and respected platform for statiscal analysis

Like many programming languages (e.g., python, Java, C++), R is based on an object-oriented language (called S). This means that all basic units in R are known as "objects". In other words, an object in R is ANY INPUT (e.g., numbers, letters, logical arguments, etc). 

### Installing R
* [Windows](https://cran.r-project.org/doc/manuals/r-release/R-admin.html#Installing-R-under-Windows)
* [Linux or Mac OS](https://cran.r-project.org/doc/manuals/r-release/R-admin.html#Installing-R-under-Unix_002dalikes)

### Running R

There are a variety of GUI (Graphical User Interface) options for running R. Among the most popular is [RStudio](https://rstudio.com/). However, you can also run R directly from your terminal. To open up a R workspace, open a terminal and type R at the prompt. You should see a similar message to the one below if R is installed correctly. The ```>``` or carrot symbol is your R prompt where you will type in all commands. 

```R
R version 3.3.1 (2016­06­21) "Bug in Your Hair"

Copyright (C) 2016 The R Foundation for Statistical Computing
Platform: x86_64­pc­linux­gnu (64­bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.  

Natural language support but running in an English locale

R is a collaborative project with many contributors. 
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on­line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

>
```

For fun, type in ```demo(graphics)``` to see some of the graphic capabilities of default R

### More R resources
* [Official R homepage](https://www.r-project.org/)
* [R for beginners (free!) book](https://cran.r-project.org/doc/contrib/Paradis-rdebuts_en.pdf)

### Some important definitions in R
* *Vector* = a one dimensional array or collection of objects that are **all of the same type**
* *Function* = a set of instructions written in the R syntax that are to be carried out on an object or elements of an object
* *Argument* = user provided values to be used in a function
* *Parameter* = a variable that stores arguments passed to your function (similar to arguments, sometimes used interchangeably)
* *Operator* = a symbol that indicates some meaning or relationship among objects
* *String* = a character or characters (e.g., words, sentences, letters)
* *Int* = short for "integer", whole numbers
* *Float* = floating point numbers (e.g., 4.0 is a float, 4 is an int)

### Types of operators (not a complete list)
* ```<-``` or ```->``` or ```=``` = assigns something to an object
* ```~``` = assigns relationships between objects, often in formulas
* ```:``` = assigns some sequence (usually of numbers)
* ```$``` = indicates that the object on the right of the operator is a component of object on left of operator (e.g., column from a dataframe)
* ```""``` or ```''``` = object is a string or character
* ```#``` = comment (R will ignore any text that follows a comment)

Math operators: ```+ - * / ^```
Comparison operators ```< > >= <= == !=```

### Five commandments for naming objects in R:
1. Objects MUST begin with a letter - this is good practice in any case, never give sample IDs or other variables in your datasets numerical names - many programs, including R will treat them in unexpected ways
2. Object names cannot contain operators or other special characters that R uses in its syntax, so no: ``` , - * / # % & [ ] { } spaces```
3. Be specific but brief. You should know what the object is from its name - 20 minutes from now you might not know what object ```x``` is but an object name like ```length.of.the.final.iteration.of.this.analysis``` is cumbersome to type.
4. Object names are case sensitive. ```Df1``` is not the same as ```df1```
5. If you must, separate words in your object names with either ```.``` or ```_```. So: ```toe.length``` or ```toe_length```. Or you can use "camel case", e.g., ```toeLength```. All are equally valid object names, the differences come down to aesthetics.

### R command line expressions

The basic structure of a R command is the command prompt followed by an object, the assignment operator, and some expression. Once you assign an expression or some other function or data to an object you can "call" (i.e., type out the object name) to evaluate your expression. So say we have a small dataset of big toe length and we want to store a vector that has all our observations in an object called toe.length

```R
toe.length <- c(3.5.4.3.6.7.3.3.2.5)
```

The ```c()``` is a function called concatenate. It tells R that we want each of the numbers in the parentheses to be values in our vector. We can then evaluate our object

```R
toe.length
[1] 3.0 5.0 4.0 3.0 6.0 7.0 3.0 3.0 2.5
```
