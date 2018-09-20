# Table of Contents

1.  [Functions](#functions)
    1.  [How to declare a function](#how-to-declare-a-function)
    2.  [Duck-typing in Julia](#duck-typing-in-julia)
    3.  [Mutating vs. non-mutating functions](#mutating-vs.non-mutating-functions)
    4.  [Some higher order functions](#some-higher-order-functions)
    5.  [Exercises](#exercises)

<div class="ABSTRACT">
Functions in Julia.

**Thu Sep 20 17:41:45 CDT 2018**

</div>


<a id="functions"></a>

# Functions

Topics:

1.  How to declare a function
2.  Duck-typing in Julia
3.  Mutating vs. non-mutating functions
4.  Some higher order functions


<a id="how-to-declare-a-function"></a>

## How to declare a function

Julia gives us a few different ways to write a function. The first
requires the `function` and `end` keywords

    function sayhi(name)
        println("Hi $name, it's great to see you!")
    end

    name = "Sergio";
    sayhi(name)

    sayhi (generic function with 1 method)


    Hi Sergio, it's great to see you!

    function f(x)
        (x^2)
    end

    x = rand(10);
    map(f, x)

    x = Vector(1:10);
    map(f, x)

    f (generic function with 1 method)


    10-element Array{Float64,1}:
     0.5366609790129925
     0.344540678557947
     0.31843295442348457
     0.32754570451424053
     0.17016468393461176
     0.02187529474908247
     0.4911918680548554
     0.13283930335337862
     0.19558972388688842
     0.844909037682892


    10-element Array{Int64,1}:
       1
       4
       9
      16
      25
      36
      49
      64
      81
     100

We can call either of these functions like this:

    sayhi("C-3PO")

    Hi C-3PO, it's great to see you!

    f(42)

    1764

Alternatively, we could have declared either of these functions in a
single line

    sayhi2(name) = println("Hi $name, it's great to see you!")

    sayhi2 (generic function with 1 method)

    f2(x) = x^2

    f2 (generic function with 1 method)

    sayhi2("R2D2")

    Hi R2D2, it's great to see you!

    f2(42)

    1764

Finally, we could have declared these as "anonymous" functions

    sayhi3 = name -> println("Hi $name, it's great to see you!")

    #15 (generic function with 1 method)

    f3 = x -> x^2

    #17 (generic function with 1 method)

    sayhi3("Chewbacca")

    Hi Chewbacca, it's great to see you!

    f3(42)

    1764


<a id="duck-typing-in-julia"></a>

## Duck-typing in Julia

*"If it quacks like a duck, it's a duck."* Julia functions will just
work on whatever inputs make sense. For example, `sayhi` works on the
name of this minor tv character, written as an integer&#x2026;

    sayhi(55595472)

    Hi 55595472, it's great to see you!

And `f` will work on a matrix.

    A = rand(3, 3)
    A

    3×3 Array{Float64,2}:
     0.893785  0.239299  0.248672
     0.524892  0.878067  0.771191
     0.709431  0.83372   0.618918
    3×3 Array{Float64,2}:
     0.893785  0.239299  0.248672
     0.524892  0.878067  0.771191
     0.709431  0.83372   0.618918

    f(A)

    3×3 Array{Float64,2}:
     1.10087  0.631326  0.560713
     1.47714  1.53957   1.28499
     1.51077  1.41783   1.20243

`f` will also work on a string like "hi" because `*` is defined for
string inputs as string concatenation.

    f("hi")

    "hihi"

On the other hand, `f` will not work on a vector. Unlike `A^2`, which is
well-defined, the meaning of `v^2` for a vector, `v`, is ambiguous.

    v = rand(3)

    3-element Array{Float64,1}:
     0.26949887384325555
     0.890390713676924
     0.4139908009026383

    f(v)

    ERROR: MethodError: no method matching ^(::Array{Float64,1}, ::Int64)
    Closest candidates are:
      ^(!Matched::Float16, ::Integer) at math.jl:782
      ^(!Matched::Missing, ::Integer) at missing.jl:120
      ^(!Matched::Missing, ::Number) at missing.jl:93
      ...
    Stacktrace:
     [1] macro expansion at ./none:0 [inlined]
     [2] literal_pow at ./none:0 [inlined]
     [3] f(::Array{Float64,1}) at ./none:2
     [4] top-level scope at none:0


<a id="mutating-vs.non-mutating-functions"></a>

## Mutating vs. non-mutating functions

By convention, functions followed by `!` alter their contents and
functions lacking `!` do not.

For example, let's look at the difference between `sort` and `sort!`.

    v = [3, 5, 2]

    3-element Array{Int64,1}:
     3
     5
     2

    sort(v)

    3-element Array{Int64,1}:
     2
     3
     5

    v

    3-element Array{Int64,1}:
     3
     5
     2

`sort(v)` returns a sorted array that contains the same elements as `v`,
but `v` is left unchanged.

On the other hand, when we run `sort!(v)`, the contents of v are sorted
within the array `v`.

    sort!(v)

    3-element Array{Int64,1}:
     2
     3
     5

    v

    3-element Array{Int64,1}:
     2
     3
     5


<a id="some-higher-order-functions"></a>

## Some higher order functions


### map

`map` is a "higher-order" function in Julia that *takes a function* as
one of its input arguments. `map` then applies that function to every
element of the data structure you pass it. For example, executing

    map(f, [1, 2, 3])

    3-element Array{Int64,1}:
     1
     4
     9

will give you an output array where the function `f` has been applied to
all elements of `[1, 2, 3]`

    [f(1), f(2), f(3)]

    3-element Array{Int64,1}:
     1
     4
     9

    map(f, [1, 2, 3])

    3-element Array{Int64,1}:
     1
     4
     9

Here we've squared all the elements of the vector `[1, 2, 3]`, rather
than squaring the vector `[1, 2, 3]`.

To do this, we could have passed to `map` an anonymous function rather
than a named function, such as

    x -> x^3

    #19 (generic function with 1 method)

via

    map(x -> x^3, [1, 2, 3])

    3-element Array{Int64,1}:
      1
      8
     27

and now we've cubed all the elements of `[1, 2, 3]`!


### broadcast

`broadcast` is another higher-order function like `map`. `broadcast` is
a generalization of `map`, so it can do every thing `map` can do and
more. The syntax for calling `broadcast` is the same as for calling
`map`

    broadcast(f, [1, 2, 3])

    3-element Array{Int64,1}:
     1
     4
     9

and again, we've applied `f` (squared) to all the elements of
`[1, 2, 3]` - this time by "broadcasting" `f`!

Some syntactic sugar for calling `broadcast` is to place a `.` between
the name of the function you want to `broadcast` and its input
arguments. For example,

    broadcast(f, [1, 2, 3])

    3-element Array{Int64,1}:
     1
     4
     9

is the same as

    f.([1, 2, 3])

    3-element Array{Int64,1}:
     1
     4
     9

    f.([1, 2, 3])

    3-element Array{Int64,1}:
     1
     4
     9

Notice again how different this is from calling

    f([1, 2, 3])

    ERROR: MethodError: no method matching ^(::Array{Int64,1}, ::Int64)
    Closest candidates are:
      ^(!Matched::Float16, ::Integer) at math.jl:782
      ^(!Matched::Missing, ::Integer) at missing.jl:120
      ^(!Matched::Missing, ::Number) at missing.jl:93
      ...
    Stacktrace:
     [1] macro expansion at ./none:0 [inlined]
     [2] literal_pow at ./none:0 [inlined]
     [3] f(::Array{Int64,1}) at ./none:2
     [4] top-level scope at none:0

We can square every element of a vector, but we can't square a vector!

To drive home the point, let's look at the difference between

    f(A)

    3×3 Array{Float64,2}:
     1.10087  0.631326  0.560713
     1.47714  1.53957   1.28499
     1.51077  1.41783   1.20243

and

    f.(A)

    3×3 Array{Float64,2}:
     0.798852  0.057264  0.061838
     0.275511  0.771002  0.594735
     0.503292  0.695089  0.383059

for a matrix `A`:

    A = [(i + (3 * j)) for j in 0:2, i in 1:3]

    3×3 Array{Int64,2}:
     1  2  3
     4  5  6
     7  8  9

    f(A)

    3×3 Array{Int64,2}:
      30   36   42
      66   81   96
     102  126  150

As before we see that for a matrix, `A`,

    f(A) = A^2 = A * A

    ERROR: syntax: "2" is not a valid function argument name

On the other hand,

    B = f.(A)

    3×3 Array{Int64,2}:
      1   4   9
     16  25  36
     49  64  81

contains the squares of all the entries of `A`.

This dot syntax for broadcasting allows us to write relatively complex
compound elementwise expressions in a way that looks natural/closer to
mathematical notation. For example, we can write

    A .+ 2 .* f.(A) ./ A

    3×3 Array{Float64,2}:
      3.0   6.0   9.0
     12.0  15.0  18.0
     21.0  24.0  27.0

instead of

    broadcast(x -> x + 2 * f(x) / x, A)

    3×3 Array{Float64,2}:
      3.0   6.0   9.0
     12.0  15.0  18.0
     21.0  24.0  27.0

and this will still compile down to code that runs as efficiently as
`C`!


<a id="exercises"></a>

## Exercises


### Exercise 1

Write a function that adds 1 to its input.

    function addOne(x)
        x + 1
    end

    addOne (generic function with 1 method)


### Exercise 2

Use `map` or `broadcast` to increment every element of matrix `A` by
`1`.

    broadcast(addOne, A)

    3×3 Array{Int64,2}:
     2  3   4
     5  6   7
     8  9  10


### Exercise 3

Use the broadcast dot syntax to increment every element of matrix `A` by
`1`.

    addOne.(A)

    3×3 Array{Int64,2}:
     2  3   4
     5  6   7
     8  9  10

*EOF*
