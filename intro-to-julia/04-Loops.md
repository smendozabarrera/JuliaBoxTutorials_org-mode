# Table of Contents

1.  [Loops](#loops)
    1.  [while loops](#while-loops)
    2.  [for loops](#for-loops)

<div class="ABSTRACT">
Loops in Julia.

**Tue Sep 11 05:10:28 CDT 2018**

</div>


<a id="loops"></a>

# Loops

Topics: 1. `while` loops 2. `for` loops


<a id="while-loops"></a>

## while loops

The syntax for a `while` is

    while *condition*
        *loop body*
    end

For example, we could use `while` to count or to iterate over an array.

    n = 0
    while n < 10
        global n += 1
        println(n)
    end

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10

    myfriends = ["Ted", "Robyn", "Barney", "Lily", "Marshall"]

    i = 1
    while i <= length(myfriends)
        friend = myfriends[i]
        println("Hi $friend, it's great to see you!")
        global i += 1
    end

    5-element Array{String,1}:
     "Ted"
     "Robyn"
     "Barney"
     "Lily"
     "Marshall"

    1
    Hi Ted, it's great to see you!
    Hi Robyn, it's great to see you!
    Hi Barney, it's great to see you!
    Hi Lily, it's great to see you!
    Hi Marshall, it's great to see you!


<a id="for-loops"></a>

## for loops

The syntax for a `for` loop is

    for *var* in *loop iterable*
        *loop body*
    end

We could use a for loop to generate the same results as either of the
examples above:

    for n in 1:10
        println(n)
    end

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10

    myfriends = ["Ted", "Robyn", "Barney", "Lily", "Marshall"]

    for friend in myfriends
        println("Hi $friend, it's great to see you!")
    end

    5-element Array{String,1}:
     "Ted"
     "Robyn"
     "Barney"
     "Lily"
     "Marshall"

    Hi Ted, it's great to see you!
    Hi Robyn, it's great to see you!
    Hi Barney, it's great to see you!
    Hi Lily, it's great to see you!
    Hi Marshall, it's great to see you!

Now let's use `for` loops to create some addition tables, where the
value of every entry is the sum of its row and column indices.

First, we initialize an array with zeros.

    m, n = 5, 5
    A = fill(0, (m, n))

    (5, 5)
    5×5 Array{Int64,2}:
     0  0  0  0  0
     0  0  0  0  0
     0  0  0  0  0
     0  0  0  0  0
     0  0  0  0  0

    for i in 1:m
        for j in 1:n
            A[i, j] = i + j
        end
    end
    A


    5×5 Array{Int64,2}:
     2  3  4  5   6
     3  4  5  6   7
     4  5  6  7   8
     5  6  7  8   9
     6  7  8  9  10

Here's some syntactic sugar for the same nested `for` loop

    B = fill(0, (m, n))

    5×5 Array{Int64,2}:
     0  0  0  0  0
     0  0  0  0  0
     0  0  0  0  0
     0  0  0  0  0
     0  0  0  0  0

    for i in 1:m, j in 1:n
        B[i, j] = i + j
    end
    B


    5×5 Array{Int64,2}:
     2  3  4  5   6
     3  4  5  6   7
     4  5  6  7   8
     5  6  7  8   9
     6  7  8  9  10

The more "Julia" way to create this addition table would have been with
an *array comprehension*.

    C = [i + j for i in 1:m, j in 1:n]

    5×5 Array{Int64,2}:
     2  3  4  5   6
     3  4  5  6   7
     4  5  6  7   8
     5  6  7  8   9
     6  7  8  9  10


### Exercises


#### Example 1

Loop over integers between 1 and 100 and print their squares.

    F = fill(1, 1);
    for i in 2:100
        push!(F, i^2)
    end
    F



    100-element Array{Int64,1}:
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
         ⋮
      8464
      8649
      8836
      9025
      9216
      9409
      9604
      9801
     10000

    [i^2 for i in 1:100]

    100-element Array{Int64,1}:
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
         ⋮
      8464
      8649
      8836
      9025
      9216
      9409
      9604
      9801
     10000


#### Example 2

Add to the code above a bit to create a dictionary, `squares` that holds
integers and their squares as key, value pairs such that

    # squares[10] == 100
    E = Dict("1" => 1);
    for i in 2:100
        E[string(i)] = i^2
    end
    E


    Dict{String,Int64} with 100 entries:
      "32" => 1024
      "29" => 841
      "1"  => 1
      "54" => 2916
      "78" => 6084
      "81" => 6561
      "2"  => 4
      "74" => 5476
      "41" => 1681
      "65" => 4225
      "51" => 2601
      "53" => 2809
      "27" => 729
      "75" => 5625
      "42" => 1764
      "33" => 1089
      "28" => 784
      "50" => 2500
      "52" => 2704
      ⋮    => ⋮


#### Example 3

Use an array comprehension to create an an array that stores the squares
for all integers between 1 and 100.

    [i^2 for i in 1:100]

    100-element Array{Int64,1}:
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
         ⋮
      8464
      8649
      8836
      9025
      9216
      9409
      9604
      9801
     10000

*EOF*
