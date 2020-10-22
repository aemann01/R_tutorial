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
