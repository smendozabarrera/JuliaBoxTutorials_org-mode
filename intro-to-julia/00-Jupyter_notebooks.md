# Table of Contents

1.  [Org-mode documents with Julia](#getting-started-with-org-mode-julia)
    1.  [Running a cell](#running-a-cell)
    2.  [How to get docs for Julia functions](#how-to-get-docs-for-julia-functions)
    3.  [How to use shell commands](#how-to-use-shell-commands)

<div class="ABSTRACT">
How to run some cells in org mode.

**Sat Sep  8 17:34:37 CDT 2018**.

</div>


<a id="getting-started-with-org-mode-julia"></a>

# Org-mode documents with Julia


<a id="running-a-cell"></a>

## Running a cell

To execute code within a cell, `C-c C-c` above.

    1 + 1
    2 + 2

    2
    4

If you're new to org-mode, note that only the last line of a
cell prints by default when you execute that cell and that you can
suppress this output with a semicolon

    1 + 1
    2 + 2;

    2


<a id="how-to-get-docs-for-julia-functions"></a>

## How to get docs for Julia functions

To get docs for a function you're not familiar with, precede it with a
question mark. (This works better at the REPL too!)

    ?println


<a id="how-to-use-shell-commands"></a>

## How to use shell commands

Type `;` and then you can use shell commands. For example,

    ;ls

    ;pwd

Shell commands also work at the REPL!

*EOF*
