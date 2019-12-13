# Genetic Programming with Propel

## The Problem
Given a vector of numbers (integers or floats), the program should return
the largest possible combination of the numbers using only the math operators **+**, **-**, **/**, and **x**.

The program should not use parentheses, but should be able to manipulate the order of the integers given.

I chose this problem because there certainly exists a "correct" solution, but it is not obvious the best way to solve it. 

<hr>

## Setting up the problem

### The program has access to these instructions 
#### **Integers**:
    integer_+
    integer_-
    integer_*
    integer_%
    integer_=

#### **Booleans**:
    boolean_and
    boolean_or
    boolean_not
    boolean_=

#### **Exec**:
    'exec_dup
    'exec_if

Vectors of 4 numbers each are given as the programs input. These are compared against a single output that is the correct largest combination. Lexicase selection was used to determine error values.

<hr>

## Results

**For each iteration of the problem, I will show the lowest error solution and give information about it's selection function and the program generated.**

### Initial runs
#### Initial runs were often relatively far from a solution.

#### Given these inputs: 
    [10 -5 5 0.5] [1 2 3 4] [-1 -2 -3 -4] [4 3 2 1] [-0.5 0.5 1 1.5] [-1 2 -3 4]  
    
The average "Best Error" was around 30. Here is the best program made given these inputs and using lexicase selection.
```
-------------------------------------------------------
               Report for Generation 500
-------------------------------------------------------
Best plushy: (close integer_% 1 in3 exec_dup in1 boolean_or integer_% 0 boolean_= in4 integer_= integer_% true integer_% integer_* boolean_or integer_+ integer_= in3 integer_- in3 integer_% integer_= in1 integer_+ false close boolean_= boolean_= integer_= in4 integer_% in1 1 false integer_+ false integer_* integer_+ false integer_* in4 boolean_and integer_% integer_+ in2 exec_if 1 close false close integer_+ in4 integer_+ in4 integer_*)
Best program: (integer_% 1 in3 exec_dup (in1 boolean_or integer_% 0 boolean_= in4 integer_= integer_% true integer_% integer_* boolean_or integer_+ integer_= in3 integer_- in3 integer_% integer_= in1 integer_+ false) boolean_= boolean_= integer_= in4 integer_% in1 1 false integer_+ false integer_* integer_+ false integer_* in4 boolean_and integer_% integer_+ in2 exec_if (1) (false) integer_+ in4 integer_+ in4 integer_*)
Best total error: 5.262148148148124
Best errors: (0.1139999999999759 53/54 0N 7/2 0.666666666666667 0N)
Best behaviors: (199.88600000000002 1297/54 24N 43/2 3.833333333333333 24N)
```

#### Given these inputs: 
    [10 -5 5 0.5] [1 2 3 4] [4 3 2 1] [0.5 5 -5 10]`    

The average "Best Error" was around 15-20. Here is the best program made given these inputs and using tournament selection.
```
-------------------------------------------------------
               Report for Generation 500
-------------------------------------------------------
Best plushy: (false 0 1 in4 in4 close integer_+ integer_- integer_- in4 integer_* boolean_= in1 in3 integer_- in4 integer_% in1 0 boolean_or integer_+ integer_+ in1 boolean_and boolean_= integer_* integer_+ integer_*)
Best program: (false 0 1 in4 in4 integer_+ integer_- integer_- in4 integer_* boolean_= in1 in3 integer_- in4 integer_% in1 0 boolean_or integer_+ integer_+ in1 boolean_and boolean_= integer_* integer_+ integer_*)
Best total error: 12.974999999999994
Best errors: (0.0 7/2 0 9.474999999999994)
Best behaviors: (200.0 57/2 25 190.525)
```
#### Given these inputs:
    [10 -5 5 0.5] [1 2 3 4] [4 3 2 1] [0.5 5 -5 10]
    [2 4 6 8] [8 6 2 4] [1 7 5 3] [3 5 7 1]
    [-3 -2 -4 -1] [-4 -3 -2 -1] [0.5 0.5 0.5 0.5] [0.5 0.5 0.5 0.5]
    [0.5 0.4 0.4 0.2] [0.4 0.2 0.5 0.4] [0 1 2 3] [3 1 2 0]
    [20 500 -1 0.2] [-1 0.2 500 20] [-0.5 2 3 4] [3 4 2 -0.5]
    [-0.5 -2 3 4] [3 4 -2 -0.5] [-0.5 -2 -3 4] [-3 4 -2 -0.5]     

The average "Best Error" was around 1050. The errors here are difficult to compare to the previous ones because of the greatly increased amount of test cases, but these programs were slightly better than the previous ones. Here is the best program made given these inputs and using lexicase selection.
```
-------------------------------------------------------
               Report for Generation 500
-------------------------------------------------------
Best plushy: (boolean_and boolean_or integer_+ boolean_= in4 close boolean_not false boolean_not false 0 boolean_or exec_if true exec_dup exec_if false in3 in3 integer_+ close integer_- in1 integer_% 0 exec_if boolean_or in1 in4 boolean_and exec_if in2 integer_- 0 integer_+ integer_+ integer_* 0 integer_= integer_* exec_if in3 in1 integer_- in3 in2 in4 integer_* in1 boolean_and false integer_* integer_*)
Best program: (boolean_and boolean_or integer_+ boolean_= in4 boolean_not false boolean_not false 0 boolean_or exec_if (true exec_dup (exec_if (false in3 in3 integer_+) (integer_- in1 integer_% 0 exec_if (boolean_or in1 in4 boolean_and exec_if (in2 integer_- 0 integer_+ integer_+ integer_* 0 integer_= integer_* exec_if (in3 in1 integer_- in3 in2 in4 integer_* in1 boolean_and false integer_* integer_*) ()) ()) ()))) ())
Best total error: 569.4533333333334
Best errors: (200.5 1 1 0.0 0 0 1 1 0 0 5.0 5.0 31.57 32.25 7 7 50.8 31 23.5 23.833333333333332 0.0 48.666666666666664 74.0 25.333333333333332)
Best behaviors: (-0.5 24 24 200.0 384 384 105 105 24 24 -1.0 -1.0 -0.32000000000000006 -1.0 0 0 0.2 20 48.0 0.6666666666666665 48.0 -0.6666666666666665 -48.0 0.6666666666666665)
```

<hr>

### Adding some functionality
After not many improvements were made among many tests    

    integer_dup
was added to the list of instructions. This allows the program to make copies of the numbers given to it.     

Along with that, to promote conditionals in the program    

    exec_if
was added to the list of instructions multiple times. Because the program needs to have many conditionals to perform correctly, exec_if needs to be used liberally.

#### Given the same extended list of inputs from earlier:

The average "Best Error" was around 850. Here is the best program made given these inputs and using lexicase selection.

```
-------------------------------------------------------
               Report for Generation 500
-------------------------------------------------------
Best plushy: (1 integer_dup in4 integer_% in3 in1 integer_+ exec_if exec_if in4 in3 boolean_not integer_* integer_* in1 in1 in1 integer_+ in2 integer_+ in1 integer_* exec_dup boolean_and integer_+ integer_+ integer_+)
Best program: (1 integer_dup in4 integer_% in3 in1 integer_+ exec_if (exec_if (in4 in3 boolean_not integer_* integer_* in1 in1 in1 integer_+ in2 integer_+ in1 integer_* exec_dup (boolean_and integer_+ integer_+ integer_+)) ()) ())
Best total error: 473.12299999999993
Best errors: (0.5 117/4 37 29.599999999999994 153/8 475/4 14/3 2 31 4 0.5 0.5 23.978 26.77 19/3 19 25.2 8.700000000000003 5.75 2.5 15.75 15.0 18.25 29.0)
Best behaviors: (200.5 217/4 62 229.6 3225/8 1061/4 304/3 108 -7 28 4.5 4.5 7.272 4.48 40/3 26 25.8 42.3 30.25 27.0 32.25 33.0 44.25 -3.0)
```

Making these changes did make non-marginal improvements to the program.

<hr>

### Expanding the error values

Still, the programs were nowhere near solving the problem, so changes were made to the error function.

The error now penalizes numbers that aren't whole, in addition to the previous error function that simply checked how far from the correct solution each program was.    

Along with this, the inputs were changed to give only whole numbers as correct answers. This was done to simplify the problem and hopefully generate some closer solutions.

<hr>

#### Given these inputs and the new error function:

    [10 -5 5 0.5] [1 2 3 4] [4 3 2 1] [0.5 5 -5 10]
    [2 4 6 8] [8 6 2 4] [1 7 5 3] [3 5 7 1]
    [-3 -2 -4 -1] [-4 -3 -2 -1] [0.5 0.5 0.5 0.5] [0.5 0.5 0.5 0.5]
    [5 4 5 3] [4 5 5 3] [0 1 2 3] [3 1 2 0]
    [2 5 -1 0.2] [-1 0.2 5 2] [-1 2 3 4] [3 4 2 -1]
    [-0.5 -2 3 4] [3 4 -2 -0.5] [-0.5 -2 -3 4] [-3 4 -2 -0.5]

The average "Best Error" was around 650. Here is the best program made given these inputs and using Tournament selection.

-------------------------------------------------------
               Report for Generation 500
-------------------------------------------------------
Best plushy: (in2 in1 in4 exec_if boolean_= integer_* integer_+ in1 integer_* exec_if in4 in4 exec_dup in3 integer_* boolean_not in1 exec_dup in1 exec_if exec_dup integer_+)
Best program: (in2 in1 in4 exec_if (boolean_= integer_* integer_+ in1 integer_* exec_if (in4 in4 exec_dup (in3 integer_* boolean_not in1 exec_dup (in1 exec_if (exec_dup (integer_+)) ()))) ()) ())
Best total error: 514.4
Best errors: (5.0 41 45 1.0 34 16 12 46 12 18 1.0 1.0 25 70 11 23 40.2 7.200000000000003 13 1 4.0 50.5 3.0 34.5)
Best behaviors: (195.0 66 70 199.0 418 400 118 152 12 6 3.0 3.0 275 230 18 30 10.8 43.8 38 24 44.0 -2.5 29.0 -8.5)

<hr>

## Closing
### Observations
* Lexicase selection often generated much better programs than tournament selection.
* Before being given negative numbers, a solution that solved the problem was generated relatively quickly, but this solution was not actually correct.
* Negative numbers might complicate the problem too much to solve in a reasonable amount of time.
* Programs were often much shorter when given only four vectors. This did not make programs _better_.
* In most cases, tournament selection didn't generate a single correct output but had a smaller error value, while lexicase would often get some of the tests correct but had high error values for the ones that were wrong.
* Changing the error generation seemed to be the biggest factor in generating more correct programs.



