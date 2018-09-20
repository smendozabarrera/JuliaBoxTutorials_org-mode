# Table of Contents

1.  [Data structures](#data-structures)
    1.  [Tuples](#tuples)
    2.  [Dictionaries](#dictionaries)
    3.  [Arrays](#arrays)
    4.  [Exercises](#exercises)

<div class="ABSTRACT">
Data Structures.

**Mon Sep 10 06:36:18 CDT 2018**.

</div>


<a id="data-structures"></a>

# Data structures

Once we start working with many pieces of data at once, it will be
convenient for us to store data in structures like arrays or
dictionaries (rather than just relying on variables).

Types of data structures covered:

1.  Tuples
2.  Dictionaries
3.  Arrays

As an overview, tuples and arrays are both ordered sequences of
elements (so we can index into them). Dictionaries and arrays are both
mutable. We'll explain this more below!


<a id="tuples"></a>

## Tuples

We can create a tuple by enclosing an ordered collection of elements in
`( )`.

Syntax: `julia (item1, item2, ...)`

    myfavoriteanimals = ("penguins", "cats", "sugargliders")

    ("penguins", "cats", "sugargliders")

We can index into this tuple,

    myfavoriteanimals[1]
    myfavoriteanimals[3]

    "penguins"
    "sugargliders"

but since tuples are immutable, we can't update it

    myfavoriteanimals[1] = "otters"

    ERROR: MethodError: no method matching setindex!(::Tuple{String,String,String}, ::String, ::Int64)
    Stacktrace:
     [1] top-level scope at none:0

What is a sugar glider, you ask? Let's download an image of one and look
at it!

    if !isfile("../../../graphs/sugar-glider.jpg")
        download("https://upload.wikimedia.org/wikipedia/commons/0/0d/Petaurus_breviceps-Cayley.jpg", "../../../graphs/sugar-glider.jpg")
    end

    load("../../../graphs/sugar-glider.jpg")

    500×396 Array{RGB{N0f8},2} with eltype RGB{Normed{UInt8,8}}:
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)        …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.992,0.992,0.992)  RGB{N0f8}(0.992,0.992,0.992)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.988,0.988,0.988)  RGB{N0f8}(0.988,0.988,0.988)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.988,0.988,0.988)  RGB{N0f8}(0.988,0.988,0.988)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.992,0.992,0.992)  RGB{N0f8}(0.992,0.992,0.992)  …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)  …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)  …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     ⋮                                                           ⋱                                ⋮
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)        …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)        …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)        …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)

Let's install the package

    using Pkg
    Pkg.add("Images")
    Pkg.add("ImageMagick")


    Resolving package versions...
     Updating `~/.julia/environments/v1.0/Project.toml`
    [no changes]
     Updating `~/.julia/environments/v1.0/Manifest.toml`
    [no changes]
    Resolving package versions...
     Updating `~/.julia/environments/v1.0/Project.toml`
    [no changes]
     Updating `~/.julia/environments/v1.0/Manifest.toml`
    [no changes]

    # May take a little bit the first time
    using Images
    sugar_glider = load("../../../graphs/sugar-glider.jpg")



    500×396 Array{RGB{N0f8},2} with eltype RGB{Normed{UInt8,8}}:
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)        …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.992,0.992,0.992)  RGB{N0f8}(0.992,0.992,0.992)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.988,0.988,0.988)  RGB{N0f8}(0.988,0.988,0.988)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.988,0.988,0.988)  RGB{N0f8}(0.988,0.988,0.988)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.992,0.992,0.992)  RGB{N0f8}(0.992,0.992,0.992)  …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)  …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)  …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)     RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     ⋮                                                           ⋱                                ⋮
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)        …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)        …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)        …  RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)
     RGB{N0f8}(1.0,1.0,1.0)        RGB{N0f8}(1.0,1.0,1.0)           RGB{N0f8}(0.996,0.996,0.996)  RGB{N0f8}(0.996,0.996,0.996)


#### Coming in 1.0: NamedTuples

In earlier versions of Julia, we had the option to work with
`NamedTuples` via a package. In 1.0, NamedTuples will be supported in
Base Julia. Therefore you'll be able to create data structures like the
following:

    myfavoriteanimals = (bird = "penguins", mammal = "cats", marsupial = "sugargliders")

    (bird = "penguins", mammal = "cats", marsupial = "sugargliders")

Like regular `Tuples`, `NamedTuples` are ordered, so we can retrieve
their elements via indexing, such that

    myfavoriteanimals[1]

    "penguins"

will return "penguins". However, we will now also be able to access
"penguins" by keyword, via

    myfavoriteanimals.bird
    myfavoriteanimals.marsupial

    "penguins"
    "sugargliders"


<a id="dictionaries"></a>

## Dictionaries

If we have sets of data related to one another, we may choose to store
that data in a dictionary. We can create a dictionary using the `Dict()`
function, which we can initialize as an empty dictionary or one storing
key, value pairs.

Syntax: `julia Dict(key1 => value1, key2 => value2, ...)`

A good example is a contacts list, where we associate names with phone
numbers.

    myphonebook = Dict(
        "Jenny" => "867-5309",
        "Ghostbusters" => "555-2368",
        "Chini" => "2225197000"
    )

    Dict{String,String} with 3 entries:
      "Jenny"        => "867-5309"
      "Chini"        => "2225197000"
      "Ghostbusters" => "555-2368"

In this example, each name and number is a "key" and "value" pair. We
can grab Jenny's number (a value) using the associated key

    myphonebook["Chini"]

    "2225197000"

We can add another entry to this dictionary as follows

    myphonebook["Kramer"] = "555-FILK"

    "555-FILK"

Let's check what our phonebook looks like now&#x2026;

    myphonebook

    Dict{String,String} with 4 entries:
      "Jenny"        => "867-5309"
      "Kramer"       => "555-FILK"
      "Chini"        => "2225197000"
      "Ghostbusters" => "555-2368"

We can delete Kramer from our contact list - and simultaneously grab his
number - by using `pop!`

    pop!(myphonebook, "Kramer")

    "555-FILK"

    myphonebook

    Dict{String,String} with 3 entries:
      "Jenny"        => "867-5309"
      "Chini"        => "2225197000"
      "Ghostbusters" => "555-2368"

Unlike tuples and arrays, dictionaries are not ordered. So, we can't
index into them.

    myphonebook[1]

    ERROR: KeyError: key 1 not found
    Stacktrace:
     [1] getindex(::Dict{String,String}, ::Int64) at ./dict.jl:478
     [2] top-level scope at none:0

In the example above, `julia` thinks you're trying to access a value
associated with the key `1`.


<a id="arrays"></a>

## Arrays

Unlike tuples, arrays are mutable. Unlike dictionaries, arrays contain
ordered collections. We can create an array by enclosing this collection
in `[ ]`.

Syntax: `julia [item1, item2, ...]`

For example, we might create an array to keep track of my friends

    myfriends = ["Ted", "Robyn", "Barney", "Lily", "Marshall"]

    5-element Array{String,1}:
     "Ted"
     "Robyn"
     "Barney"
     "Lily"
     "Marshall"

The `1` in `Array{String,1}` means this is a one dimensional vector. An
`Array{String,2}` would be a 2d matrix, etc. The `String` is the type of
each element.

or to store a sequence of numbers

    fibonacci = [1, 1, 2, 3, 5, 8, 13]

    7-element Array{Int64,1}:
      1
      1
      2
      3
      5
      8
     13

    mixture = [1, 1, 2, 3, "Ted", "Robyn"]

    6-element Array{Any,1}:
     1
     1
     2
     3
      "Ted"
      "Robyn"

Once we have an array, we can grab individual pieces of data from inside
that array by indexing into the array. For example, if we want the third
friend listed in `myfriends`, we write

    myfriends[3]

    "Barney"

We can use indexing to edit an existing element of an array

    myfriends

    println(":: Getting third element ::")
    myfriends[3] = "Baby Bop"

    5-element Array{String,1}:
     "Ted"
     "Robyn"
     "Barney"
     "Lily"
     "Marshall"

    :: Getting third element ::
    "Baby Bop"

Yes, **Julia is 1-based indexing**, not 0-based like Python. Wars are
faught over lesser issues. I have a friend with the wisdom of Solomon
who proposes settling this once and for all with `½` :smiley:

We can also edit the array by using the `push!` and `pop!` functions.
`push!` adds an element to the end of an array and `pop!` removes the
last element of an array.

We can add another number to our fibonnaci sequence

    push!(fibonacci, 21)

    8-element Array{Int64,1}:
      1
      1
      2
      3
      5
      8
     13
     21

and then remove it

    pop!(fibonacci)

    21

    fibonacci

    7-element Array{Int64,1}:
      1
      1
      2
      3
      5
      8
     13

So far I've given examples of only 1D arrays of scalars, but arrays can
have an arbitrary number of dimensions and can also store other arrays.
For example, the following are arrays of arrays:

    favorites = [
        ["koobideh", "chocolate", "eggs"],
        ["penguins", "cats", "sugargliders"]
    ]

    2-element Array{Array{String,1},1}:
     ["koobideh", "chocolate", "eggs"]
     ["penguins", "cats", "sugargliders"]

    numbers = [
        [1, 2, 3],
        [4, 5],
        [6, 7, 8, 9]
    ]

    3-element Array{Array{Int64,1},1}:
     [1, 2, 3]
     [4, 5]
     [6, 7, 8, 9]

Below are examples of 2D and 3D arrays populated with random values.

    rand(4, 3)

    4×3 Array{Float64,2}:
     0.0187732  0.725403  0.774366
     0.27996    0.186569  0.638738
     0.158637   0.193291  0.755511
     0.374137   0.594866  0.0319379

    rand(4, 3, 2)

    4×3×2 Array{Float64,3}:
    [:, :, 1] =
     0.0409652   0.7521    0.332586
     0.34334     0.657881  0.478918
     0.00927325  0.590553  0.961698
     0.249506    0.931815  0.250351

    [:, :, 2] =
     0.459657  0.779721   0.7211
     0.481826  0.109121   0.993989
     0.739129  0.151485   0.848454
     0.384884  0.0365876  0.974311

Be careful when you want to copy arrays!

    fibonacci

    7-element Array{Int64,1}:
      1
      1
      2
      3
      5
      8
     13

    somenumbers = fibonacci

    7-element Array{Int64,1}:
      1
      1
      2
      3
      5
      8
     13

    somenumbers[1] = 404

    404

    fibonacci

    7-element Array{Int64,1}:
     404
       1
       2
       3
       5
       8
      13

Editing `somenumbers` caused `fibonacci` to get updated as well!

In the above example, we didn't actually make a copy of `fibonacci`. We
just created a new way to access the entries in the array bound to
`fibonacci`.

If we'd like to make a copy of the array bound to `fibonacci`, we can
use the `copy` function.

    # First, restore fibonacci
    fibonacci[1] = 1
    fibonacci


    1
    7-element Array{Int64,1}:
      1
      1
      2
      3
      5
      8
     13

    somemorenumbers = copy(fibonacci)

    7-element Array{Int64,1}:
      1
      1
      2
      3
      5
      8
     13

    somemorenumbers[1] = 404

    404

    fibonacci

    7-element Array{Int64,1}:
      1
      1
      2
      3
      5
      8
     13

In this last example, fibonacci was not updated. Therefore we see that
the arrays bound to `somemorenumbers` and `fibonacci` are distinct.


<a id="exercises"></a>

## Exercises


### Example 1

Create an array, `a_ray`, with the following code:

    a_ray = [1, 2, 3]

    3-element Array{Int64,1}:
     1
     2
     3

Add the number `4` to the end of this array and then remove it.

    println(":: Add a number 4 at the end of the array ::")
    push!(a_ray, 4)
    a_ray

    println(":: Remove the last cell ::")
    pop!(a_ray)

    println(":: Show the array ::")
    a_ray

    :: Add a number 4 at the end of the array ::
    4-element Array{Int64,1}:
     1
     2
     3
     4
    4-element Array{Int64,1}:
     1
     2
     3
     4

    :: Remove the last cell ::
    4

    :: Show the array ::
    3-element Array{Int64,1}:
     1
     2
     3


### Example 2

Try to add "Emergency" as key to `myphonebook` with the value
`string(911)` with the following code

    myphonebook
    myphonebook["Emergency"] = 911

    Dict{String,String} with 3 entries:
      "Jenny"        => "867-5309"
      "Chini"        => "2225197000"
      "Ghostbusters" => "555-2368"
    ERROR: MethodError: Cannot `convert` an object of type Int64 to an object of type String
    Closest candidates are:
      convert(::Type{T<:AbstractString}, !Matched::T<:AbstractString) where T<:AbstractString at strings/basic.jl:207
      convert(::Type{T<:AbstractString}, !Matched::AbstractString) where T<:AbstractString at strings/basic.jl:208
      convert(::Type{T}, !Matched::T) where T at essentials.jl:154
    Stacktrace:
     [1] setindex!(::Dict{String,String}, ::Int64, ::String) at ./dict.jl:381
     [2] top-level scope at none:0

Why doesn't this work?


#### Answer error message

ERROR: MethodError: Cannot \`convert\` an object of type Int64 to an
object of type String


### Example 3

Create a new dictionary called `flexible_phonebook` that has Jenny's
number stored as an integer and Ghostbusters' number stored as a string
with the following code

    flexible_phonebook = Dict(
        "Jenny" => 8675309,
        "Ghostbusters" => "555-2368"
    )

    Dict{String,Any} with 2 entries:
      "Jenny"        => 8675309
      "Ghostbusters" => "555-2368"


### Example 4

Add the key "Emergency" with the value `911` (an integer) to
`flexible_phonebook`.

    flexible_phonebook["Emergency"] = 911
    flexible_phonebook

    911
    Dict{String,Any} with 3 entries:
      "Jenny"        => 8675309
      "Emergency"    => 911
      "Ghostbusters" => "555-2368"


### Example 5

Why can we add an integer as a value to `flexible_phonebook` but not
`myphonebook`? How could we have initialized `myphonebook` so that it
would accept integers as values?


#### Answer

Because `Julia` is strongly typed syntax:

`Dict{String,Any}`

in the flexible array defined with type `Any`.

*EOF*
