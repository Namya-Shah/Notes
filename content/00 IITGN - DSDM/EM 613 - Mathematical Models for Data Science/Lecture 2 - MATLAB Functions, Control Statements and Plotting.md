---
Lecture Date: 2024-06-07
Presentation: "[[Lecture 2.pdf]]"
Links:
  - "[[MATLAB]]"
Subject:
  - "[[EM 613 - Mathematical Models for Data Science]]"
tags:
  - Matlab
  - EM613
---
```table-of-contents
```
# MATLAB Functions

- Functions
    - A function is a reusable block of code that performs a specific task or computation
    - Variables defined in a function are local to that function
    - A function performs the specific task only when called
- Why use functions?
    - To avoid duplicate blocks of code
    - Separate complex operations
    - Make error identification and debugging easier
    - Promote program reuse
	![[Lecture 2.png]]
# Inbuilt Functions

| det | Determinant of a square matrix (numerically and symbolically) |
| --- | --- |
| diag | Diagonal of a square matrix; creates a diagonal matrix |
| dot | Dot product of two vectors |
| eig | Eigenvalues and Eigenvectors of special matrix equations |
| end | Last index in an array |
| eye | Creates the identity matrix |
| find | Finds indices of a vector satisfying a logical expression |
| fliplr | Flips elements of an array from left to right |
| flipud | Flips elements of an array from bottom to top |
| inv | Inverse of a square matrix (numerically and symbolically) |
| length | Length of a vector |
| magic | Creates a square matrix whose sum of each row, each column, and diagonals is equal |
| max | Determines the maximum value in an array |
| min | Determines the minimum value in an array |
| ones | Creates an array whose elements equal 1 |
| plot | Plots curves in a plane using linear axes |
| rank | Estimates number of linearly independent rows or columns of a matrix |
| repmat | Replicates arrays |
| size | Order (size) of an array |
| sort | Sorts elements of an array in ascending order |
| sum | Sums elements of an array |
| zeros | Creates an array whose elements equal 0 |

# User-Defined Functions

- Syntax of a user-defined function:

```matlab
function [outputvariables] = FunctionName (inputvariables)

Expressions

outputvariables = results; % Assign the results to outputvariables
end
```

- **function:** Keyword to specify a function file
- *outputvariables:* One or more variables that will be returned by the function
- ***FunctionName***: This is the name given to the function. In MATLAB, a function file is saved under the same name as that of the function
- *inputvariables*: The (local) variables which the function will use for its computation
	![[Lecture 2 1.png]]


- Write a function that computes the functions *x* and *y* where

$$
x = cos(at) + b\\
y = |x| + c
$$

- **Solution:**
    - Here, *a, b,* and *c* are scalars
    - *t, x,* and *y* are vectors
    - The function must accept *t,a,b,c* as input and return *x,y* as output
    - Let us name the function ComputeXY
        
    ```matlab
        function[x,y] = ComputeXY(t,a,b,c)
        	% ComputeXY accepts t as a vector, and a,b,c as scalars
        	% ComputeXY returns x,y as row vectors
        	x = cos(a*t) + b;
        	y = abs(x) + c;
        end
        ```
        

# Alternate Ways

![[Lecture 2 2.png]]
# Nested Functions

- Syntax of nested functions:

```matlab
function [*outputvariables*] = ***FunctionName1*** (*inputvariables*)
	Expressions
	function [*outputvariables*] = ***FunctionName2*** (*inputvariables)
	...*
	end
end	**
```

- Further, multiple functions can be written in a single function file
- Filename must be the same as that of the first function
	![[Lecture 2 3.png]]


# Anonymous functions

- These are means to create functions for simple expressions without having to create function files
- To shorten the code
- Can be created using @ symbol in the command window script file, primary function or a subfunction
- Syntax: **functionhandle** = @(arguments) (expression)
- Here,
    - **functionhandle** is the handle of the function, i.e., a variable that stores the association to a function
    - arguments is a comma-separated list of variable names
    - expression is a valid MATLAB expression
	![[Lecture 2 4.png]]
# Function Handle

y = @(arguments)(expression)

- So, here `y` is the function handle
- We can make a function handle from user-defined functions

## Steps to use user-defined functions as function handle

1. Create a user-defined function file. Here, the file name would be mypower.m
    
    ```matlab
    function r = mypower(x)
        r = square(x) - x.^3;
    end
    
    function r1 = square(x)
        r1 = x.^2;
    end
    ```
    
2. Create another function file whose function you want to call
    
    ```matlab
    function r = evaluate(fn,x)
        r = fn(x);
    end
    ```
    
3. Now, you print the output
    
    ```matlab
    evaluate(@mypower,x)
    ```
    
- To make a function a function handle, you need to use @
- In anonymous function, as we use @ before arguments and expression. So, we can pass that anonymous function without @ in the function

# Plotting

- We use `plot()` to plot a graph
- `gca` → Get Current Axis
- `gcf` → Get Current Figure
- We can label using `xlabel()` and `ylabel()`
- We can also have legend using `legend()`
- We can modify the axis using `axis`
- To make the axis square we can use `axis square`
- We can also use marker to decorate our charts
- If we want to change the axis values on x axis, we can use `xlim` and for y axis, we can use `ylim`

# Control Statements

## Program Flow Control

- Selection Statements
    - `if` statement
    - `if else` statement
    - Nested `if` statement
    - `switch` statement
- Iterative statements
    - `for` loop
    - `while` loop
        - `break` statement
        - `continue` statement
- `for` and `switch` statements are similar
- In a range of conditions we will use `while` or `if else`

## Selection statements - if
	![[Lecture 2 5.png]]

- `if` statement
    - Used to execute statements only if the condition is satisfied
- Syntax
    
    ![[Lecture 2 6.png]]
- Example
    
	 ![[Lecture 2 7.png]]   

## Selection Statements - if else


	![[Lecture 2 8.png]]
- `if else` statement
    - Used to execute one set of statements if a condition is satisfied, and another set of statements, otherwise
- Syntax
    
    ![[Lecture 2 9.png]]
    

## Selection statements - Nested if

![[Lecture 2 10.png]]

- Nested `if` statement
    - if-else condition within if-else condition
- Syntax
    
    ![[Lecture 2 11.png]]
    
- Not to use too many conditional statements and it also becomes complicated

## Selection statements - switch
	![[Lecture 2 12.png]]

- `switch` statement
    - Execute a particular set of statements based on the value of an expression
- Syntax
    
    ![[Lecture 2 13.png]]
    

## Iterative statements - while loop

![[Lecture 2 14.png]]

- `while` loop
    - `while` loops allow repeated execution of a code snippet as long as a specified condition is met
    - Syntax
        
        ![[Lecture 2 15.png]]
        
    - `while` loops are used when the number of iterations are not known beforehand
    - It is important to ensure that the *condition* eventually becomes false to prevent infinite loop

## Iterative statements - for loop

![[Lecture 2 16.png]]

- `for` loop
    - `for` loops allow repeated execution of a code snippet over a specified number of times
    - Syntax
        
        ![[Lecture 2 17.png]]
        
    - Here, *values* stores the data over which *index* iterates
    - *values* can be a scalar or a vector
    - It has to be ensured that *values* contains integers ≥ 1, if *index* is to be used to access an array element

## break and continue statements

![[Lecture 2 18.png]]

- `break` statement
    - A `break` statement is used to control the flow of the statement
    - It is used to exit a loop prematurely, even if the loop condition is still true
- `continue` statement
    - A `continue` statement is used to skip the current iteration of a loop and move to the next iteration
    - Helps in increasing code efficiency by skipping unnecessary computations

# Plots in MATLAB: 2-D Plots

![[Lecture 2 19.png]]

- **Syntax:** `plot(*xdata,ydata,options)*`
- **Line specifications**
    - `'LineWidth'` : Change the thickness of the line
    - `'LineStyle'` : Change the type of line plotted, to make it dotted, or solid, or a dash-dot line
        - E.g.: “-”, “--”, “:”, “-.”
    - `'Marker'` : Add special symbols called markers on the curve
        - E.g.: “o”, “+”, “square”, “.”
    - `'Color'` : Changes the color of the curve
        - E.g.: “r”, “g”, “b”, “k”, “m”, “c”, “y”
- **Axes properties**
    - `xlabel` : Name the x-axis
    - `ylabel` : Name the y-axis
    - `xlim()` : Used to plot the graph within certain limits on the x-axis
    - `ylim()` : Used to plot the graph within certain limits on the y-axis
    - `gca` : Returns the current graphical axes
        - The properties of the axes can be modified using the `gca` command
        - `set()` function can be used to alter the properties of the axes object
        - We can write `set(gca)` to know what we can set for the axes
        - We can get the properties of the axes using `get(gca)`

![[Lecture 2 20.png]]

- We can clear axis using `cla` . We can clear the figure using `clf` .
- We can create the figure using `figure` or `gcf`
- We can create axis using `gca`

# Some other useful plots in MATLAB

![Untitled](Lecture%202%20MATLAB%20Functions,%20Control%20Statements%20and%207a0d1b6e6745484991e043ba3f871c8b/Untitled%2021.png)

- `surf(X,Y,S)`
    - Creates a 3D surface whose height S is a function of X and Y
- `mesh(X,Y,S)`
    - Creates a 3D wireframe mesh
- `contour(X,Y,C)`
    - Creates contour plot containing isolines of matrix C
- `streamline(X,Y,Z,U,V,W,xstart,ystart,zstart)`
    - Creates 3D plot of streamlines that begin at `xstart` , `ystart` and `zstart`
- `quiver(X,Y,U,V)`
    - Plots arrows with directional components U and V