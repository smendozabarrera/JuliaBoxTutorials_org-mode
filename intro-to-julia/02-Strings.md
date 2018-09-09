# Table of Contents

1.  [Strings](#strings)
    1.  [How to get a string](#how-to-get-a-string)
    2.  [String interpolation](#string-interpolation)
    3.  [String concatenation](#string-concatenation)

<div class="ABSTRACT">
Strings in Julia.

**Sat Sep  8 18:32:32 CDT 2018**.

</div>


<a id="strings"></a>

# Strings

**Topics**:

1.  How to get a string
2.  String interpolation
3.  String concatenation


<a id="how-to-get-a-string"></a>

## How to get a string

Enclose your characters in `" "` or `""" """`!

    s1 = "I am a string."

    "I am a string."

    s2 = """I am also a string. """

    "I am also a string. "

There are a couple functional differences between strings enclosed in
single and triple quotes. One difference is that, in the latter case,
you can use quotation marks within your string.

    "Here, we get an "error" because it's ambiguous where this string ends "

    ERROR: syntax: cannot juxtapose string literal

    """Look, Mom, no "errors"!!! """

    "Look, Mom, no \"errors\"!!! "

Note that `' '` define a character, but NOT a string!

    typeof('a')

    Char

    'We will get an error here'

    ERROR: syntax: invalid character literal


<a id="string-interpolation"></a>

## String interpolation

We can use the `$` sign to insert existing variables into a string and to
evaluate expressions within a string. Below is an example that contains
some highly sensitive personal information.

    name = "Jane"
    num_fingers = 10
    num_toes = 10

    "Jane"
    10
    10

    println("Hello, my name is $name.")
    println("I have $num_fingers fingers and $num_toes toes.")

    Hello, my name is Jane.
    I have 10 fingers and 10 toes.

    println("That is $(num_fingers + num_toes) digits in all!!")

    That is 20 digits in all!!


<a id="string-concatenation"></a>

## String concatenation

Below are three ways we can concatenate strings! The first way is to use
the `string()` function. `string()` converts non-string inputs to
strings.

    s3 = "How many cats ";
    s4 = "is too many cats?";
    😺 = 10



    10

    string(s3, s4)

    "How many cats is too many cats?"

    string("I don't know, but ", 😺, " is too few.")

    "I don't know, but 10 is too few."

We can also use `*` for concatenation!

    s3 * s4

    "How many cats is too many cats?"


### Exercises


#### Exercise 1

Create a string that says "hi" 1000 times, first with `repeat` and then
with the exponentiation operator, which can call `*` under the hood.


##### From the [documentation](https://docs.julialang.org/en/v1/base/strings/#Base.repeat-Tuple{AbstractString,Integer})

    n = 10
    repeat("hi", n)

    10
    "hihihihihihihihihihi"

    "hi"^n

    "hihihihihihihihihihi"


#### Exercise 2

Declare two variables

    a = 3
    b = 4

    3
    4

and use them to create two strings:

    string(a, " + ", b)
    string(a + b)

    "3 + 4"
    "7"

*EOF*
