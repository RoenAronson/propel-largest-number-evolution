# Genetic Programming with Propel

## The Problem
Given a vector of numbers (integers or floats), the program should return
the largest possible combination of the numbers using only the math operators **+**, **-**, **/**, and **x**.

The program should not use parentheses, but should be able to manipulate the order of the integers given.

I chose this problem because there certainly exists a "correct" solution, but it is not obvious the best way to solve it. 

==========================================================================================================================

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

## Results
### Initial runs
#### Initial runs were often relatively far from a solution.

#### Given these inputs: 
    `[10 -5 5 0.5] [1 2 3 4] [-1 -2 -3 -4] [4 3 2 1] [-0.5 0.5 1 1.5] [-1 2 -3 4]`  
    
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

## Closing
### Observations
* Lexicase selection often generated much better programs than tournament selection.
* Before being given negative numbers, a correct solution was generated relatively quickly.
* Negative numbers might complicate the problem too much to solve in a reasonable amount of time.



