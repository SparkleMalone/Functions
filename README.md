# Introduction to writing Functions in R

Functions are essential tools in R. Functions eliminate repetition from your code, which can reduce your workload, and help you to avoid errors. Here’s what you need to know about creating and calling them and more. It is very important to understand the purpose and syntax of R functions and knowing how to create or use them. In this tutorial, we'll learn what an R function is, what types of functions exist in R, when we should use a function, how to create and call a user-defined function.

### What Is a Function in R?
A function in R is an object containing multiple interrelated statements that are run together in a predefined order every time the function is called. Functions in R can be built-in or user-defined. The main purpose of creating a user-defined function is to optimize scripts and avoid repetition. A good practice is creating a function whenever you need to run a certain set of commands more than twice.

### Built-in Functions in R
Some of the most popular built in function are:
•	min(), max(), mean(), median(): returns the minimum / maximum / mean / median value of a numeric vector
•	sum(): returns the sum of a numeric vector
•	range(): returns the minimum and maximum values of a numeric vector
•	abs(): returns the absolute value of a number
•	str(): shows the structure of an R object
•	print(): displays an R object on the console
•	ncol(): returns the number of columns of a matrix or a dataframe
•	length(): returns the number of items in an R object (a vector, a list, etc.)
•	nchar(): returns the number of characters in a character object
•	sort(): sorts a vector in ascending or descending (decreasing=TRUE) order
•	exists():returns TRUE or FALSE depending on whether or not a variable is defined in the R environment

### Creating a Function in R
While applying built-in functions facilitates many common tasks, often we need to create our own function to automate the performance of a particular task. To declare a user-defined function in R, we use the keyword function. The syntax is as follows:

  function_name <- function(parameters){
    function body 
  }

### 1. Function Name
This is the name of the function object that will be stored in the R environment. After the function is defined, the function name is used for calling that function. It should be concise but clear and meaningful so that the user who reads our code can easily understand what exactly this function does. It is common to use verbs in function names and it is also ok to use a noun if that noun is very descriptive and unambiguous.

### 2. Function Parameters
Function parameters are the variables in the function definition placed inside the parentheses and separated with a comma that will be set to actual values (called arguments) each time we call the function.

### 3. Function Body
The function body is a set of commands inside the curly braces that are run in a predefined order every time we call the function. In the function body, we place what exactly we need the function to do. For example, we can create a function to sum two numbers listed as parameters x and y: 

```{r, echo=TRUE}
sum_two_nums <- function(x, y){
    x + y
}

print(sum_two_nums(1, 2))

```


Next, lets create a function to calculate the circumference of a circle with a known radius. The function has only one parameter r. 

```{r, echo=TRUE}

  circumference <- function(radius){
    2*pi*radius
  }
```

After defining the function, call it with the radius equal to 2:

```{r, echo=TRUE}
circumference( r=2)

```

It's possible, even though rarely useful, for a function to have no parameters:

```{r}

hello_world <- function(){
    'Hello, World!'
}

print(hello_world())

```
Also, some parameters can be set to default values inside the function definition, which then can be reset when calling the function. Returning the circumference function, we can set the default radius of a circle to 1. If we call the function with no argument passed, it will calculate the circumference of a  a circle with a radius of 1. Otherwise, it will calculate the circumference of a circle with the provided radius:

```{r}

circumference <- function(r=1){
    2*pi*r
}

print(circumference())

print(circumference( r=2))
```

Note that the statements in the function body should be indented by 2 or 4 spaces, depending on the IDE where we run the code, but the important thing is to be consistent with the indentation throughout the program. While it doesn't affect the code performance and isn't obligatory, it makes the code easier to read.

### return()
As we saw from all the above examples, in R, it usually isn't necessary to explicitly include the return statement when defining a function since an R function just automatically returns the last evaluated expression in the function body. However, we still can add the return statement inside the function body using the syntax return(expression_to_be_returned). This becomes inevitable if we need to return more than one result from a function. For example:

```{r}
mean_median <- function(vector){
    mean <- mean(vector)
    median <- median(vector)
    return(c(mean, median))
}

print(mean_median(c(1, 1, 1, 2, 3)))
```

Note that in the return statement above, we actually return a vector containing the necessary results, and not just the variables separated by a comma (since the return() function can return only a single R object). Instead of a vector, we could also return a list, especially if the results to be returned are supposed to be of different data types.

## Calling a Function in R
In all the above examples, we actually already called the created functions many times. To do so, we just put the punction name and added the necessary arguments inside the parenthesis. In R, function arguments can be passed by position, by name (so-called named arguments), by mixing position-based and name-based matching, or by omitting the arguments at all.
If we pass the arguments by position, we need to follow the same sequence of arguments as defined in the function:

```{r}
subtract_two_nums <- function(x, y){
    x - y
}

print(subtract_two_nums(3, 1))
```
In the above example, x is equal to 3 and y – to 1, and not vice versa.

If we pass the arguments by name, i.e., explicitly specify what value each parameter defined in the function takes, the order of the arguments doesn't matter:
  
  ```{r}
  subtract_two_nums <- function(x, y){
    x - y
  }
  print(subtract_two_nums(x=3, y=1))
  print(subtract_two_nums(y=1, x=3))
```

Things to remember when using functions inside other functions: If you want to be able to use the function independent of another function, it should be created outside a function instead of nesting the functions. 

Assessment:

(This tutorial utilized https://www.dataquest.io/blog/write-functions-in-r/)
