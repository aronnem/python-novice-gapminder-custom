---
title: "Comparisons and Conditionals"
teaching: 10
exercises: 10
questions:
- "How can programs do different things for different data?"
objectives:
- "Correctly write programs that use if and else statements and simple Boolean expressions (without logical operators)."
- "Trace the execution of unnested conditionals and conditionals inside loops."
keypoints:
- "Use `if` statements to control whether or not a block of code is executed."
- "Conditionals are often used inside loops."
- "Use `else` to execute a block of code when an `if` condition is *not* true."
- "Use `elif` to specify additional tests."
- "Conditions are tested once, in order."
- "Create a table showing variables' values to trace a program's execution."
---

# Comparisons
 - It is often useful to compare two objects
    - For example, checking whether a data point is above the mean
 - Python has many special operators for comparison
 - Comparisons return `True` or `False`
    - `True` and `False` are called **Boolean types**

## Comparing numbers
  - Use `==` to check whether two numbers are equal
  - Use `!=` to check whether two number are unequal
  - `>`, `>=`, `<`, `<=` check whether one number is greater than greater or less than a number (with or without equality)
  - For example, the following comparisons all return `True`
    ~~~
    3 == 3
    5.0 != 1
    10.0 > 1.0
    10 >= 10
    10 <= 10
    1 < 5
    ~~~
    {: .python}

## Comparing collections
 - Just like numbers, `==` and `!=` can be used to check whether two collections are the same or different
    - Collections are only equal if they are of the same type!
 - Additionally, **membership** can be checked using the operators `in` and `not in`

~~~
small_primes = [2, 3, 5, 7, 11]
3 in small_primes       # True
4 in small_primes       # False

4 not in small_primes   # True
5 not in small_primes   # False
~~~
{: .python}

## Check whether a value is (or is not) `None` using `is` (or `is not`)

> ## Use `None` to represent missing or null data
>
> - It is sometimes useful to indicate that data does not exist
> - For example, how would you add a person with only one name to the following list
>
> ~~~
> people = [('Taylor', 'Scott'), ('Patrick', 'Shirwise'), ('Matt', 'Garcia'), ('Kalin', 'Kiesling')]
> ~~~
> {: .python}
>
> - It's best to add the new person as a tuple with two values. One of the values can be `None`
>
> ~~~
> people.append(('Elvis', None))
> print(people)
> ~~~
> {: .python}
> ~~~
> [('Taylor', 'Scott'), ('Patrick', 'Shirwise'), ('Matt', 'Garcia'), ('Kalin', 'Kiesling'), ('Elvis', None)]
> ~~~
> {: .output}
{: .discussion}

 - The operators `is` and `is not` check whether data is `None`
 - You should only use `is` and `is not` when comparing to `None`

 ~~~
 ('Elvis', None)[0] is None     # False
 ('Elvis', None)[1] is None     # True
 ~~~
 {: .python}


# Conditionals

## Use `if` statements to control whether or not a block of code is executed.

*   An `if` statement (more properly called a *conditional* statement)
    controls whether some block of code is executed or not.
*   Structure is similar to a `for` statement:
    *   First line opens with `if` followed by a comparison and ends with a colon
    *   Body containing one or more statements is indented (usually by 4 spaces)

~~~
mass = 3.54
if mass > 3.0:
    print(mass, 'is large')

mass = 2.07
if mass > 3.0:
    print (mass, 'is large')
~~~
{: .python}
~~~
3.54 is large
~~~
{: .output}

## Conditionals are often used inside loops.

*   Not much point using a conditional when we know the value (as above).
*   But useful when we have a collection to process.

~~~
masses = [3.54, 2.07, 9.22, 1.86, 1.71]
for m in masses:
    if m > 3.0:
        print(m, 'is large')
~~~
{: .python}
~~~
3.54 is large
9.22 is large
~~~
{: .output}

## Use `else` to execute a block of code when an `if` condition is *not* true.

*   `else` can be used following an `if`.
*   Allows us to specify an alternative to execute when the `if` *branch* isn't taken.

~~~
masses = [3.54, 2.07, 9.22, 1.86, 1.71]
for m in masses:
    if m > 3.0:
        print(m, 'is large')
    else:
        print(m, 'is small')
~~~
{: .python}
~~~
3.54 is large
2.07 is small
9.22 is large
1.86 is small
1.71 is small
~~~
{: .output}

## Use `elif` to specify additional tests.

*   May want to provide several alternative choices, each with its own test.
*   Use `elif` (short for "else if") and a condition to specify these.
*   Always associated with an `if`.
*   Must come before the `else` (which is the "catch all").

~~~
masses = [3.54, 2.07, 9.22, 1.86, 1.71]
for m in masses:
    if m > 9.0:
        print(m, 'is HUGE')
    elif m > 3.0:
        print(m, 'is large')
    else:
        print(m, 'is small')
~~~
{: .python}
~~~
3.54 is large
2.07 is small
9.22 is HUGE
1.86 is small
1.71 is small
~~~
{: .output}

## Conditions are tested once, in order.

*   Python steps through the branches of the conditional in order, testing each in turn.
*   So ordering matters.

~~~
grade = 85
if grade >= 70:
    print('grade is C')
elif grade >= 80:
    print('grade is B')
elif grade >= 90:
    print('grade is A')
~~~
{: .python}
~~~
grade is C
~~~
{: .output}

*   Does *not* automatically go back and re-evaluate if values change.

~~~
velocity = 10.0
if velocity > 20.0:
    print('moving too fast')
else:
    print('adjusting velocity')
    velocity = 50.0
~~~
{: .python}
~~~
adjusting velocity
~~~
{: .output}

*   Often use conditionals in a loop to "evolve" the values of variables.

~~~
velocity = 10.0
for i in range(5): # execute the loop 5 times
    print(i, ':', velocity)
    if velocity > 20.0:
        print('moving too fast')
        velocity = velocity - 5.0
    else:
        print('moving too slow')
        velocity = velocity + 10.0
print('final velocity:', velocity)
~~~
{: .python}
~~~
0 : 10.0
moving too slow
1 : 20.0
moving too slow
2 : 30.0
moving too fast
3 : 25.0
moving too fast
4 : 20.0
moving too slow
final velocity: 30.0
~~~
{: .output}

## Create a table showing variables' values to trace a program's execution.

<table>
  <tr>
    <td><strong>i</strong></td>
    <td>0</td>
    <td>.</td>
    <td>1</td>
    <td>.</td>
    <td>2</td>
    <td>.</td>
    <td>3</td>
    <td>.</td>
    <td>4</td>
    <td>.</td>
  </tr>
  <tr>
    <td><strong>velocity</strong></td>
    <td>10.0</td>
    <td>20.0</td>
    <td>.</td>
    <td>30.0</td>
    <td>.</td>
    <td>25.0</td>
    <td>.</td>
    <td>20.0</td>
    <td>.</td>
    <td>30.0</td>
  </tr>
</table>

*   The program must have a `print` statement *outside* the body of the loop
    to show the final value of `velocity`,
    since its value is updated by the last iteration of the loop.

> ## Compound Relations Using `and`, `or`, and Parentheses
>
> Often, you want some combination of things to be true.  You can combine
> relations within a conditional using `and` and `or`.  Continuing the example
> above, suppose you have
>
> ~~~
> mass     = [ 3.54,  2.07,  9.22,  1.86,  1.71]
> velocity = [10.00, 20.00, 30.00, 25.00, 20.00]
>
> i = 0
> for i in range(5):
>     if mass[i] > 5 and velocity[i] > 20:
>         print("Fast heavy object.  Duck!")
>     elif mass[i] > 2 and mass[i] <= 5 and velocity[i] <= 20:
>         print("Normal traffic")
>     elif mass[i] <= 2 and velocity <= 20:
>         print("Slow light object.  Ignore it")
>     else:
>         print("Whoa!  Something is up with the data.  Check it")
> ~~~
> {: .python}
>
> Just like with arithmetic, you can and should use parentheses whenever there
> is possible ambiguity.  A good general rule is to *always* use parentheses
> when mixing `and` and `or` in the same condition.  That is, instead of:
>
> ~~~
> if mass[i] <= 2 or mass[i] >= 5 and velocity[i] > 20:
> ~~~
> {: .python}
>
> write one of these:
>
> ~~~
> if (mass[i] <= 2 or mass[i] >= 5) and velocity[i] > 20:
> if mass[i] <= 2 or (mass[i] >= 5 and velocity[i] > 20):
> ~~~
> {: .python}
>
> so it is perfectly clear to a reader (and to Python) what you really mean.
{: .callout}

> ## Tracing Execution
>
> What does this program print?
>
> ~~~
> pressure = 71.9
> if pressure > 50.0:
>     pressure = 25.0
> elif pressure <= 50.0:
>     pressure = 0.0
> print(pressure)
> ~~~
> {: .python}
{: .challenge}

> ## Trimming Values
>
> Fill in the blanks so that this program creates a new list
> containing zeroes where the original list's values were negative
> and ones where the origina list's values were positive.
>
> ~~~
> original = [-1.5, 0.2, 0.4, 0.0, -1.3, 0.4]
> result = ____
> for value in original:
>     if ____:
>         result.append(0)
>     else:
>         ____
> print(result)
> ~~~
> {: .python}
>
> ~~~
> [0, 1, 1, 1, 0, 1]
> ~~~
> {: .output}
{: .challenge}


> ## Initializing
>
> Modify this program so that it finds the largest and smallest values in the list
> no matter what the range of values originally is.
>
> ~~~
> values = [...some test data...]
> smallest, largest = None, None
> for v in values:
>     if ____:
>         smallest, largest = v, v
>     ____:
>         smallest = min(____, v)
>         largest = max(____, v)
> print(smallest, largest)
> ~~~
> {: .python}
>
> What are the advantages and disadvantages of using this method
> to find the range of the data?
{: .challenge}

{: .callout}
