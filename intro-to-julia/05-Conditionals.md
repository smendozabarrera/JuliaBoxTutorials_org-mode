# Table of Contents

1.  [Conditionals](#conditionals)
    1.  [With the `if` keyword](#with-the-if-keyword)
    2.  [with ternary operators](#with-ternary-operators)
    3.  [With short-circuit evaluation](#with-short-circuit-evaluation)
    4.  [This means we can use](#org93720b5)
2.  [Exercises](#exercises)
    1.  [Example 1](#section)
    2.  [Example 2](#section-1)

<div class="ABSTRACT">
Conditionals in Julia.

**Tue Sep 11 05:10:28 CDT 2018**

</div>


<a id="conditionals"></a>

# Conditionals


<a id="with-the-if-keyword"></a>

## With the `if` keyword

In Julia, the syntax

    if *condition 1*
        *option 1*
    elseif *condition 2*
        *option 2*
    else
        *option 3*
    end

allows us to conditionally evaluate one of our options. For example, we
might want to implement the FizzBuzz test: given a number, N, print
"Fizz" if N is divisible by 3, "Buzz" if N is divisible by 5, and
"FizzBuzz" if N is divisible by 3 and 5. Otherwise just print the number
itself!

    N = 150

    150

    if (N % 3 == 0) & (N % 5 == 0)
        println("FizzBuzz")
    elseif N % 3 == 0
        println("Fizz")
    elseif N % 5 == 0
        println("Buzz")
    else
        println(N)
    end

    FizzBuzz


<a id="with-ternary-operators"></a>

## with ternary operators

For this last block, we could instead use the ternary operator with the
syntax

    a ? b : c

which equates to

    if a
        b
    else
        c
    end

Now let's say we want to return the larger of two numbers. Using the
`if` and `else` keywords, we might write

    x = 120
    y = 121

    120
    121

    if x > y
        x
    else
        y
    end

    121

and as a ternary operator, the conditional looks like this:

    (x > y) ? x : y

    121


<a id="with-short-circuit-evaluation"></a>

## With short-circuit evaluation

We've already seen expressions with the syntax

    a & b

for two expressions or values `a` and `b`. Julia will evaluate this
expression eagerly so that

    false & (println("hi"); true)

    hi
    false

prints "hi" to stdout before returning false.

On the other hand, when we replace `&` with `&&`, as in

    a && b

we get short-circuit evaluation. `b` is only evaluated if `a` is true,
which can help us out if evaluating `b` is expensive. For example,

    false && (println("hi"); true)

    false

returns `false` without printing "hi".


<a id="org93720b5"></a>

## This means we can use

    a && b

**to conditionally evaluate `b` if `a` is true!**

    (x > y) && println(x)

    false

    (x < y) && println(y)

    121

Similarly, check out the difference between

    true | (println("hi"); true)

    hi
    true

and

    true || (println("hi"); true)

    true

where `|` means `or`.


<a id="exercises"></a>

# Exercises


<a id="section"></a>

## Example 1

Write a conditional statement that prints a number if the number is even
and the string "odd" if the number is odd.

    number = 121;

    if (number % 2 == 0)
        println(number)
    else
        println("odd")
    end



    odd


<a id="section-1"></a>

## Example 2

Rewrite the code from 5.1 using a ternary operator.

    number = 22;
    (number % 2 == 0) ? number : "odd"


    22

*EOF*
