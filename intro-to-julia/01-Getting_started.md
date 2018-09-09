# Table of Contents

1.  [Getting started](#getting-started)
    1.  [How to print](#how-to-print)
    2.  [How to assign variables](#how-to-assign-variables)
    3.  [How to comment](#how-to-comment)
    4.  [Syntax for basic math](#syntax-for-basic-math)
    5.  [Exercises](#exercises)

<div class="ABSTRACT">
How to run some cells in org mode.

**Sat Sep  8 17:34:37 CDT 2018**.

</div>


<a id="getting-started"></a>

# Getting started

**Topics**:

1.  How to print
2.  How to assign variables
3.  How to comment
4.  Syntax for basic math


<a id="how-to-print"></a>

## How to print

In Julia we usually use `println()` to print

    println("I'm excited to learn Julia!")

    I'm excited to learn Julia!


<a id="how-to-assign-variables"></a>

## How to assign variables

All we need is a variable name, value, and an equal's sign! Julia will
figure out types for us.

    my_answer = 42
    typeof(my_answer)

    42
    Int64

    my_pi = 3.14159
    typeof(my_pi)

    3.14159
    Float64

    😺 = "smiley cat!"
    typeof(😺)

    "smiley cat!"
    String

To type a smiley cat, use tab completion to select the emoji name and
then tab again

    # \:smi + <tab> --> select with down arrow + <enter> ---> <tab> + <enter> to complete

After assigning a value to a variable, we can reassign a value of a
different type to that variable without any issue.

      😺 = 1

    1

    typeof(😺)

    Int64

Note: Julia allows us to write super generic code, and 😺 is an example
of this.

This allows us to write code like

      😀 = 0
      😞 = -1

    0
    -1

      😺 + 😞 == 😀

    true


<a id="how-to-comment"></a>

## How to comment

    # You can leave comments on a single line using the pound/hash key

    #=

    For multi-line comments,
    use the '#= =#' sequence.

    =#


<a id="syntax-for-basic-math"></a>

## Syntax for basic math

    sum = 3 + 7

    10

    difference = 10 - 3

    7

    product = 20 * 5

    100

    quotient = 100 / 10

    10.0

    power = 10 ^ 2

    100

    modulus = 101 % 2

    1


<a id="exercises"></a>

## Exercises


### Exercise 1

Look up [docs](https://docs.julialang.org/en/v1) for the `convert` function.

    a = 3
    typeof(a)
    a = convert(Float64, a)
    typeof(a)

    3
    Int64
    3.0
    Float64


### Exercise 2

Assign `365` to a variable named `days`. Convert `days` to a float.

    days = 365
    typeof(days)
    days = convert(Float64, days)
    typeof(days)

    365
    Int64
    365.0
    Float64


### Exercise 3

See what happens when you execute

    convert(Int64, "1")

    ERROR: MethodError: Cannot `convert` an object of type String to an object of type Int64
    Closest candidates are:
      convert(::Type{T<:Number}, !Matched::T<:Number) where T<:Number at number.jl:6
      convert(::Type{T<:Number}, !Matched::Number) where T<:Number at number.jl:7
      convert(::Type{T<:Integer}, !Matched::Ptr) where T<:Integer at pointer.jl:23
      ...
    Stacktrace:
     [1] top-level scope at none:0

**An error rise because this try to cast a character to an `Int64`**.

and

    parse(Int64, "1")

    1

**This successfully cast the character to a `Int64`**

*EOF*
