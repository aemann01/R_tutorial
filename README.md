# Beginner R Programming for Anthropologists (and other folks too!)

NOTE: still under construction as readme file, see 00-scratch for full materials

Allison E. Mann, last updated March 22, 2021

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
toe.length <- c(3, 5, 4, 3, 6, 7, 3, 3, 2.5)
```

The ```c()``` is a function called concatenate. It tells R that we want each of the numbers in the parentheses to be values in our vector. We can then evaluate our object

```R
toe.length
[1] 3.0 5.0 4.0 3.0 6.0 7.0 3.0 3.0 2.5
```

You'll notice that R did something unexpected here. Remember that vectors much be a collection of objects of all the same type. Since we included a floating point element (2.5) R will automatically convert all of your elements to floats. Be aware of this!! Floats are often not treated the same as integers mathmatically.

We can now use some of R's built in functions to further evaluate our new object. So for example if we wanted to know the mean value:

```R
> mean(toe.length)
[1] 4.055556
```

Or maybe we want to know how long (i.e., how many elements) are in our object (this is really useful for loops which we'll talk about more below)

```R
> length(toe.length)
[1] 9
```

### Object classes

Knowing the class of your object is important as R treats different classes of objects in different ways.

1. Numeric --> integers, floats
2. Characters --> strings, letters, numbers
3. Boolean --> TRUE, FALSE
4. Vector --> a single dimension of some type of objects
5. Matrix --> a multidimensional collection of objects (all of the same kind)
6. Data Frame --> a multidimensional collection of objects (with each column representing different variables, can be objects of different types)
7. List --> collection of objects that have different classes (e.g., a collection of numbers and strings)
8. Factor --> a categorical (factorial) class of objects (e.g., if you have a variable that is male and female this would be a factor with two variables)

If you're not sure what class of object you are working with you can check with:

```R
> class(toe.length)
[1] "numeric"
```

Let's get some more detailed information about our object:

```R
> str(toe.length)
num [1:9] 3 5 4 3 6 7 3 3 2.5
```

This command ("structure") tells us that our object toe.length is numeric, it has 9 elements, and lists the object's values as originally designated (i.e., not floats when appropriate)

What if you want to check if an object is of a particular type?

```R
> is.numeric(toe.length)
[1] TRUE
> is.character(toe.length)
[1] FALSE
```

You can also coerce your object into a different class of objects (note: since we do not assign this expression to a new object nothing changes)

```R
> as.character(toe.length)
[1] "3" "5" "4" "3" "6" "7" "3" "3" "2.5"
```

### Keeping track of your R workspace

* List the objects currently in your workspace ```> ls()```
* Remove object ```rm()```
* See the current working directory ```> getwd()```
* Set a new working directory ```> setwd()```
* See files currently in your working directory (equivalent to terminal command ls) ```> dir()```

### Installing and loading new packages in R

```R
> install.packages()
```

Running this command will bring up a list of repositories that you can choose to download from. Once you choose a repository, a list of all available libraries will load. If you already know the name of the library you want you can download them directly by typing in the name of the library surrounded by quotes:

```R
> install.packages("reshape")
> install.packages("lattice")
```

To then load these libraries into your R environment you'll need to call them directly with the ```library()``` function (notice you don't need quotation marks here)

```R
> library(reshape)
> library(lattice)
```

### Getting help

If you are unsure how to use a particular library you have a couple options. If you know the exact package name you can run the help function to open the library's documentation page (click q to quit)

```R
> help(reshape)
```

OR

```R
> ?reshape
```

If you are interested in a specific function within a package:

```R
> ??reshape::melt
```

This command will give you some basic information on the different melting options within the reshape package (e.g., converting wide-format to long-format data). You can then get some more detailed information of these again with the help command:

```R
> help(melt_check)
```

Finally, if you don't know what library or function will work for you, remember that Google is your best friend. Use the appropriate R terminology to help you track down what you are looking for!

### Loading your own data into R

Some things to remember before getting to this point -- R is finicky about how it wants your data to be formatted so it can be loaded properly. First and foremost your data should have NO EMPTY SPACES. R does not take kindly to empty cells or null values. If you need to have null values set them up as "NaN" or "NA" so that R will recognize them. Even if you load your data and get no errors, never assume that R has loaded your data properly. Always check that your values were loaded in the expected fashion (for example I find that often R will interpret a column in a dataframe as a factor when it is supposed to be numeric etc -- always check this out!).

If your data is separated by some common unit it is simple to load your data using the read.table function. Let's make a dummy file and load it into R. First use the system function to call a shell command:

```R
> system("nano file.txt")
```

Create the following file with comma delimination. Save to file by pressing CTRL+X

```bash
sample,name,length
1,moxie,24
2,laika,22
3,jackson,30
```

Now we can load the file into R

```R
> dat <- read.table("file.txt", header=TRUE, sep=",")
```

In this example you are reading in a file in your current working directory called file.txt, telling R that the first row are column headers, and that your file is comma delimited.

### A brief primer on indexing

Indexing is a way you can access slices or particular elements of your data using the ```[]``` operators. As vectors are single dimension arrays, their indexes are simpler than matrices or dataframes. So for example, if we wanted to access the 3rd element or our toe.length vector object:

```R
> toe.length[3]
[1] 4
```

Or we could grab a subset of the data

```R
> toe.length[1:4]
[1] 3 5 4 3
```

Or you could print the vector and ignore a specific value

```R
> toe.length[-4]
[1] 3.0 5.0 4.0 6.0 7.0 3.0 3.0 2.5
```

(Why do you think this printed out as floats but the other as integers?)

Indexing a multimensional array (e.g., matrix/dataframe) is a little more complex but remember that the notation always lists the index of the row first followed by the index of the column. Axis 1 == column, Axis 2 == row.

|   | 1     | 2     | 3     |
|---|-------|-------|-------|
| 1 | [1,1] | [1,2] | [1,3] |
| 2 | [2,1] | [2,2] | [2,3] |
| 3 | [3,1] | [3,2] | [3,3] |

Note: while most programming languages start indexing at 0, R starts with 1

So if we wanted to access the middle value in our example we could do it in a couple ways. First let's transform our vector into a proper matrix.

```R
mat <- matrix(toe.length, nrow=3, ncol=3)
```

How did R fill in our matrix? By columns or rows? Any interesting or unexpected outcomes? Why do you think this is?

```R
    [,1] [,2] [,3] 
[1,] 3    3  3.0 
[2,] 5    6  3.0 
[3,] 4    7  2.5
```

Let's pull out the value in the second column and third row:

```R
> mat[3,2]
[1] 7
```

If, on the other hand, you had column names you could also use them to pull values in a more intuitive way. Let's say our matrix is actually looking at toe length measured at different ages. We can assign column names like so:

```R
> colnames(mat) <- c("baby", "child", "adult")
```

If each row represented a different individual we could also change this like so:

```R
> rownames(mat) <- c("jack", "moxie", "laika")
```

And then we can covert our matrix to a more flexible dataframe (remember dataframes, unlike matrices, can have different types of data)

```R
> df <- as.data.frame(mat)
```

Now we can use the ```$``` operator to access elements in a column or the whole column

```R
> df$baby
[1] 3 5 4
> df$baby[3]
[1] 4
```

### Loops and functions in R

There are two commonly used types of loops in R. The ```for``` and ```while``` loop operators. Loops ask R to do some function multiple times according to the parameters you provide. Loops, like funcitons (more below), are bounded by curly brackets that indicate the beginning and end of the loop.

#### For loop example:

First let's initialize some values that we want to loop over

```R
mystr <- "blast off!"
```

We want to split this string into individual characters that we can iterate over. Basically what we're doing with the function below is splitting each element (including the space on its own). Also we are initializing a numeric value that we can use in our loop (iter)

```R
> split <- strsplit(str, '')[[1]]
> iter <- 1
```

Now let's create our loop

```R
> for(i in length(split)){
	countdown <- paste(i, " ", split[iter])
	print(countdown)
	iter <- iter+1
}
```

While loops are similar except in each round of the loop they evaluate whether or not a statement is true (HINT: zero is considered false in boolean logic). We can write a similar loop to the one above with some minor modifications (remember to reset any iteration objects!)

```R
> iter <- 1
> countdown <- length(split)
> while(countdown != 0){
	iter <- iter+1
	countdown <- countdown-1
	print(blastoff)
}
```

Sometimes you might find that there are no libraries/functions that currently exist to meet your needs in R. In that case you can write your own functions! The basic syntax for functions in R is as follows where the open and closed curly brackets indicate the start and end of the funtion (remember to assign your function an object name!)

```R
myfunc <- function(<arguments that will need to be passed to your function>){
	<evaluation statements>
}
```

Let's make a simple counter function that uses a loop

```R
myfunc <- function(num){
	vec <- 0
	for(i in 1:num){
		vec <- c(vec, 1)
	}
	return(vec)
}
```

To run this function we call it like any other:

```R
myfunc(5)
[1] 0 1 2 3 4 5
```

Let's try to understand what is happening under the hood of this function a little better. We open the function by assigning our starting number (vec) as zero, after which it begins a loop that will iterate over each element (i) in a series of numbers from 1 to the value of num. If we run this function with num=5 the expression ```vec <- c(vec, 1)``` is actually run five times in a loop. In each loop the value of vec is concatenated with the next value of i. So for example in pass one ```vec = 0 + 1``` in pass two ```vec = 0, 1 + 2``` pass three ```vec = 0, 1, 2 + 3``` etc. When your object vec is finally returned outside of the loop you have a full vector of six numbers ranging from zero to five.

### Playing with a real dataset

There is a dataset in this github repository called Howells_dat.csv. This dataset consists of craniometric measurements collected by William Howells from 1965 to 1980 and includes data from more than two thousand individual crania from 28 populations of varying ages. Original data was downloaded from web.utk.edu/~auerbach/HOWL.htm. Howells detailed the data collected in his 1996 American Journal of Physical Anthropology publication "Howells craniometric data on the internet". I've added some factor based climate data calculated from the purported origin of the individuals in this dataset as classified by the Köppen-Geiger climate classification system (Peel et al. 2007. Updated world map of the Köppen-Geiger climate classification. Hydrol. Earth Syst. Sci). The impact of climate on craniofacial shape is a classic anthropological question of which we can test with rich datasets such as this one. On the other hand, large datasets like this one can be difficult to explore using less flexible statistical software. R to the rescue!!

#### Step one: load in and summarize the data

Make sure you are in the correct folder

```R
> dir()
```

Take a look at your file, load into the R workspace, and attach

```R
> system("head Howell_dat.csv")
> crania <- read.table("Howell_dat.csv", header=TRUE, sep=",")
> attach(crania)
```

#### Step two: let's take a look at the data's attributes

What column names are there?

```R
> names(crania)
```

Summarize the dataset with the function summary()

```R
> summary(crania)
```

How many males and females are represented in the data? What climate variables are present? What populations are rerpesented?

#### Step three: let's start running some basic analyses

Are there any notable differences by populations (split by males and females)? Let's make a boxplot that shows this for one of the measurements (GOL)

```R
> library(lattice)
> bwplot(GOL ~ Sex | Population, xlab="Sex", ylab="GOL")
```

Any notable problems? (Hint, distribution of males and females?)

Let's split our data by sex, detach the full dataset, and only look at males 

```R
> males <- crania[Sex == "M",]
> detach(crania)
```

Let's evaluate this craniometric measurement with our male dataset by climate group

```R
> bwplot(males$GOL ~ males$climate_group)
> hist(males$GOL, prob=T)
> lines(density(males$GOL))
```

#### What if you wanted to look at all of the measurements by climate group and save each as a pdf? With a loop of course!

First let's create a vector with just our measurement names that we want to look at

```R
> names(males)
> measurement.list <- names(males)[10:79]
```

How many variables are we going to generate figures for?

```R
> str(measurement.list)
```

To not clutter up our working directory let's make a new directory to save our boxplots to

```R
> system("mkdir boxplots")
```

Now let's loop!

```R
for(i in 1:70){
	id <- measurement.list[1]
	file <- paste(id, "_climatebp.pdf", sep="")
	path <- paste("boxplots/", file, sep="")
	pdf(path)
	print(bwplot(males[,id] ~ males$climate_group, ylab=id, main=paste(id, "by Climate Group", sep=" ")))
	dev.off()
}
```

### Step four: now that you have the grasp of the basics, what other questions could you ask of this data? How would you explore this dataset further with R? Happy scripting!

