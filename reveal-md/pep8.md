# CAM and PEP 8
## Style Guide for Python Code

Note:
* People don't apply it, so the assumption is that they must not have read it
* Purpose of this talk is to go through PEP8 and allow for discussion and
  explanation of parts that may be unclear

---

# Introduction

> Code is read much more often than it is written.
~ Guido van Rossum

* A style guide is about ... **CONSISTENCY**
* Completed source code should reflect _a harmonized style_, as if a single
  developer wrote the code in one session
* But its not law
 - always use good judgement to maintain best readability

Note:
- I'd add to quote ... "and by multiple individuals"

----

## Why consistency?

* Helps improve the **quality** of the overall software system
* The more readable source code is, the easier it is for someone to
  **maintain** that code
  - Easier to grasp the context and purpose
  - Easier to find and correct bugs
* Provides a **better view** of how that code fits within the larger
  application
  -  The clearer view leads to the potential for more code reuse (a dramatic
     affect on cost and development effort)

----

## Psychological factor

* The sense of "code ownership".

 [Scott Dorman](http://geekswithblogs.net/sdorman/archive/2007/06/29/Why-Coding-Standards-Are-Important.aspx
) writes:

*"Code ownership refers to a feeling of pride about the quality of the work
done and a desire to see that code (product) do well."*

----

* The higher the sense of ownership, the better the quality becomes
* The higher the sense of ownership, the better the developer feels about his
  skills (this is particularly true for newer developers)
* The better the developer feels about his skills, the better the code
  becomes

----

*"If this sounds like a self-fulfilling prophecy, you're right. When you feel
better about yourself and the job you are able to perform, the quality of your
work increases. As your quality increases so does your sense of self-worth in
that job. This ends up creating a development team that has a strong sense of
ownership of the code and a strong desire to see that product succeed."*

----

Sun Microsystems provides the [following](http://www.oracle.com/technetwork/java/index-135089.html
) rationale:

* 40%–80% of the lifetime cost of a piece of software goes to maintenance
* Hardly any software is maintained for its whole life by the original author
* Code conventions improve the readability of the software, allowing engineers to
  understand new code more quickly and thoroughly.
* If you ship your source code as a product, you need to make sure it is as well
  packaged and clean as any other product you create.

---

# Joke break

## Coming home after work
![Coming home after work](http://67.media.tumblr.com/e56e60c34bf53f065facf244a048f74d/tumblr_inline_nmpx17YtPB1raprkq_500.gif)

----

## Chuck
* When Chuck Norris throws exceptions, it’s across the room.

* Chuck Norris’s first program was **kill -9**.

---

# Code lay-out

----

## Indentation

* 4 spaces per indentation level

*in example dot shows a space*


    if snow_falling():
    ....dress_warm()
    ....build_snow_man()
    ....if has_snow_sled():
        ....go_slide()

----

## Continuation lines

* Use Python's implicit line joining


    raise SnowBlizzardError("Failed to go outside and play "
                            "in the snow! Reason = 'Weatherman "
                            "got it wrong again'")

    list_of_frozen_characters = ['Elsa',
                                 'Anna',
                                 'Kristoff',
                                 'Pebble',
                                 'Olaf']

----

* Use *hanging indentation*
 - Rule: No arguments on first line
 - Rule: Further indentation should be clearly distinguished

No:


    # Arguments on first line forbidden when not using vertical alignment.
    foo = long_function_name(var_one, var_two,
        var_three, var_four)

    # Further indentation required as indentation is not distinguishable.
    def long_function_name(
        var_one, var_two, var_three,
        var_four):
        print(var_one)

----

Yes:


    # Aligned with opening delimiter.
    foo = long_function_name(var_one, var_two,
                             var_three, var_four)

    # More indentation included to distinguish this from the rest.
    def long_function_name(
            var_one, var_two, var_three,
            var_four):
        print(var_one)

    # Hanging indents should add a level.
    foo = long_function_name(
        var_one, var_two,
        var_three, var_four)

----

* The 4-space rule is optional for continuation lines.

Optional:


    # Hanging indents *may* be indented to other than 4 spaces. Here we
    # only make use of 2 spaces.
    foo = long_function_name(
      var_one, var_two,
      var_three, var_four)

----

### Long **if**-statements

Problem:

    # No extra indentation. Creates visual conflict with the indented
    # suite of code nested inside.
    if (this_is_one_thing and
        that_is_another_thing):
        do_something()

* PEP8 says ... "whatever"

----

Acceptable options:


    # Add a comment, which will provide some distinction in editors
    # supporting syntax highlighting.
    if (this_is_one_thing and
        that_is_another_thing):
        # Since both conditions are true, we can frobnicate.
        do_something()

    # Add some extra indentation on the conditional continuation line.
    if (this_is_one_thing
            and that_is_another_thing):
        do_something()

----

### Closing brace/bracket/parenthesis on multi-lines

* Option 1: line up under the first non-whitespace character of the last line
of list


    my_list = [
        1, 2, 3,
        4, 5, 6,
        ]

    result = some_function_that_takes_arguments(
        'a', 'b', 'c',
        'd', 'e', 'f',
        )

----

Option 2: lined up under the first character of the line that starts the
multi-line construct


    my_list = [
        1, 2, 3,
        4, 5, 6,
    ]

    result = some_function_that_takes_arguments(
        'a', 'b', 'c',
        'd', 'e', 'f',
    )

---

## Tabs or Spaces?

PEP8 says
> "spaces are the preferred indentation method"

CAM says
> "NEVER EVER use tabs for indentation!"

---

## Maximum Line Length

PEP8 says
> "Limit all lines to a maximum of 79 characters"

CAM says
> "Maximum line length is 90 characters"

---

## Blank Lines

* Surround top-level function and class definitions with two blank lines.
* Method definitions inside a class are surrounded by a single blank line.

----

Example:

    import lotr


    def locate_the_white_wizard():
       """Module function 1"""
       lotr.locate_gandalf()


    def locate_the_brown_wizard():
       """Module function 2"""
       lotr.locate_radagast()


    class MiddleEarth(object):

        def __init__(self):
            self._num_orcs = 10000
            self._num_elves = 1000
            self._num_hobbits = 100
            self._num_wizards = 14.3

        def goto_hobbiton(self):
            """Class method 1"""
            lotr.teleport('hobbiton')

        def goto_lothlorien(self):
            """Class method 2"""
            lotr.teleport('lothlorien')

---

## Source File Encoding

=> This affects how the interpreter reads the characters in the file:


    # -*- coding: utf-8 -*-

* Code in the core Python distribution should always use UTF-8 (or ASCII in
  Python 2).

* Files using ASCII (in Python 2) or UTF-8 (in Python 3) should **not** have an
  encoding declaration.

---

## Imports

* Imports on separate lines
* All module import statements (e.g. *import os*)  should be grouped
  before spelled (e.g. *from os import path*) imports

Yes:

    import os
    import sys
    from subprocess import Popen, PIPE

No:

    from subprocess import Popen, PIPE
    import sys, os

----

* The standard grouping order defined by PEP-8 is:

 1. standard library imports
 2. related third party imports
 3. local application/library specific imports

* CAM expand on this by saying:

 1. standard library imports
 2. related third party imports
 3. **'kat' package imports**
 4. local application/library specific imports

----

* Imports are always put at the top of the file
* You should put a blank line between each group of imports

----

Wildcard imports?

    from <module> import *

PEP8 says
> "Wildcard imports should be avoided"

CAM says
> "NEVER use wildcard imports!"

----

> Relative imports for intra-package imports are highly discouraged. Always use the absolute package path for all import

* Absolute imports are recommended over explicit relative imports
* Implicit relative imports should *never* be used (removed Python3)

----

## [Example](https://docs.python.org/2.5/whatsnew/pep-328.html)

Package directory:

    pkg/
    pkg/__init__.py
    pkg/main.py
    pkg/string.py

Defines a package named *pkg* containing the *pkg.main* and *pkg.string* submodules.

main.py:

    import string

Python will first look into the package's directory to perform a relative import. So it gets *pkg.string*, but what if you wanted Python's standard *string* module?  

----

Reading code which relies on relative imports is also less clear about which module, *string* or *pkg.string*, is intended to be used.

A solution: Do not duplicate the names of standard library modules in the names of your packages' submodules.

BUT what if a future Python version use the name of your submodule?

----

From Python 2.7 the absolute-import behavior is the default.

So:

    """Will find the standard library's version"""
    import string

vs

    """Nice and clear absolute import"""
    from pkg import string

----

Other absolute import examples:

    import mypkg.sibling
    from mypkg import sibling
    from mypkg.sibling import example

----

> However, explicit relative imports are an acceptable alternative to absolute imports, especially when dealing with complex package layouts where using absolute imports would be unnecessarily verbose:

Explicit relative import:

    from . import sibling
    from .sibling import example

----

### Example of imports

    # standard library imports
    import logging
    import time
    # Newline between each group

    # 3rd party imports
    import numpy
    import scipy

    # 'kat' imports
    import katcp
    import katconf
    import katcore.proxy_base
    import katcore.dev_base

    # Imports from the current package
    import katsim

    ## spelled imports
    # standard library
    from functools import partial

    # 3rd party spelled imports
    from numpy import array, zeros
    from scipy import fit

    # 'kat' spelled imports
    from katcp.core import FailReply, AsyncReply, Sensor, ProtocolFlags
    from katcp.kattypes import request, return_reply
    from katcore.dev_base import Device, SimpleModel
    from katcore import sim_base

    # spelled imports from the current package.
    # can be absolute (usually preferred):
    from katsim.mkat_cbf_model import CBFError
    # or relative if it is likely that the module structure will be changed:
    from .mkat_cbf_array_katcp import KatcpArrayController

---

# String Quotes

* In Python, single-quoted strings and double-quoted strings are the same
* Pick a rule and stick to it

### Good recommendations

- Single characters or single word constants, use a single-quoted string
- For sentences, use double-quoted strings with embedded single-quoted strings
  to provide more context

----

### Example

    if ape == 'kingkong':
        move_away_slowly()

    hairy_ape_ids = ['aws', 'wq1', 'qwqg', 'yip']

    tranquiliser_types = ['x', 'y', 'z', '-9']

    if ape_gone_mad():
        raise NYTowerWarning("Warning notice to whoever cares: 'There is a big "
                             "and angry gorilla coming your way'!")

----

For triple-quoted strings, always use double quote characters to be consistent with the docstring convention in [PEP 257](https://www.python.org/dev/peps/pep-0257/).

Yes:

    """People say nothing is impossible, but I do nothing every day."""

No:

    '''People say nothing is impossible, but I do nothing every day.'''

---

# Whitespace in Expressions and Statements

----

### Avoid extra whitespace

* Immediately inside parentheses, brackets or braces.


    Yes: spam(ham[1], {eggs: 2})
    No:  spam( ham[ 1 ], { eggs: 2 } )


* Immediately before a comma, semicolon, or colon:


    Yes: if x == 4: print x, y; x, y = y, x
    No:  if x == 4 : print x , y ; x , y = y , x

----

> However, in a slice the colon acts like a binary operator, and should have equal amounts on either side (treating it as the operator with the lowest priority). In an extended slice, both colons must have the same amount of spacing applied. Exception: when a slice parameter is omitted, the space is omitted.

----

Yes:

    ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]
    ham[lower:upper], ham[lower:upper:], ham[lower::step]
    ham[lower+offset : upper+offset]
    ham[: upper_fn(x) : step_fn(x)], ham[:: step_fn(x)]
    ham[lower + offset : upper + offset]

No:

    ham[lower + offset:upper + offset]
    ham[1: 9], ham[1 :9], ham[1:9 :3]
    ham[lower : : upper]
    ham[ : upper]

----

* Immediately before the open parenthesis that starts the argument list of a function call:


    Yes: spam(1)
    No:  spam (1)

* Immediately before the open parenthesis that starts an indexing or slicing:


    Yes: dct['key'] = lst[index]
    No:  dct ['key'] = lst [index]

----

* More than one space around an assignment (or other) operator to align it with another.


    Yes:

    x = 1
    y = 2
    long_variable = 3

    No:

    x             = 1
    y             = 2
    long_variable = 3

----

## Other Recommendations

Always surround these binary operators with a single space on either side:

- assignment: **=**
- augmented assignment: **+= , -=** etc.
- comparisons: **== , < , \> , != , <> , <= , >= , in , not in , is , is not**
- booleans: **and , or , not**

----

> If operators with different priorities are used, consider adding whitespace
around the operators with the lowest priority(ies). Use your own judgment;
however, never use more than one space, and always have the same amount of
whitespace on both sides of a binary operator.

----

Yes:

    i = i + 1
    submitted += 1
    x = x*2 - 1
    hypot2 = x*x + y*y
    c = (a+b) * (a-b)

No:

    i=i+1
    submitted +=1
    x = x * 2 - 1
    hypot2 = x * x + y * y
    c = (a + b) * (a - b)

----

Don't use spaces around the = sign when used to indicate a keyword argument or
a default parameter value.


Yes:

    def complex(real, imag=0.0):
        return magic(r=real, i=imag)

No:

    def complex(real, imag = 0.0):
        return magic(r = real, i = imag)

----

Do use spaces around the = sign of an annotated function definition.
Additionally, use a single space after the : , as well as a single space on
either side of the -> sign representing an annotated return value.

Yes:

    def munge(input: AnyStr):
    def munge(sep: AnyStr = None):
    def munge() -> AnyStr:
    def munge(input: AnyStr, sep: AnyStr = None, limit=1000):

No:

    def munge(input: AnyStr=None):
    def munge(input:AnyStr):
    def munge(input: AnyStr)->PosInt:

----

Compound statements (multiple statements on the same line) are generally discouraged.


Yes:

    if foo == 'blah':
        do_blah_thing()
    do_one()
    do_two()
    do_three()

Rather not:

    if foo == 'blah': do_blah_thing()
    do_one(); do_two(); do_three()

----

While sometimes it's okay to put an if/for/while with a small body on the same
line, never do this for multi-clause statements. Also avoid folding such long
lines!


Rather not:

    if foo == 'blah': do_blah_thing()
    for x in lst: total += x
    while t < 10: t = delay()

Definitely not:

    if foo == 'blah': do_blah_thing()
    else: do_non_blah_thing()

    try: something()
    finally: cleanup()

    do_one(); do_two(); do_three(long, argument,
                                 list, like, this)

    if foo == 'blah': one(); two(); three()

---

# Joke break

## Unit testing
![Unit Testing](http://67.media.tumblr.com/3d4c0c08b7ee1787b4cf229251632da9/tumblr_inline_no7oigASv41raprkq_500.gif)

----

## Neilen, when someone commits with the tests not passing
![Not passing](http://66.media.tumblr.com/c55d790c7c51adaa31c4a0524ea0a9d3/tumblr_inline_oauhd9j3ra1raprkq_500.gif)

----

## Chuck

* Chuck Norris’s keyboard doesn’t have a Ctrl key because nothing controls Chuck Norris.

* Chuck Norris can write infinite recursion functions … and have them return.

---

# Comments

----

## Some Rules

- Use English
- Comments that contradict the code are worse than no comments.
- Comments should be complete sentences.
    - If a comment is a phrase or sentence, its first word should be capitalized, unless it is an identifier that begins with a lower case letter (never alter the case of identifiers!).

----

- If a comment is short, the period at the end can be omitted.
    - Block comments generally consist of one or more paragraphs built out of complete sentences, and each sentence should end in a period.
- You should use two spaces after a sentence-ending period.

----

## Block Comments

    # Block comments generally apply to some (or all) code that follows
    # them, and are indented to the same level as that code. Each line
    # of a block comment starts with a # and a single space.
    #     (unless it is indented text
    #      inside the comment)
    #
    # Paragraphs inside a block comment are separated by a line
    # containing a single #.

----

## Inline Comments

- Use inline comments sparingly.
- An inline comment is a comment on the same line as a statement. Inline comments should be separated by at least two spaces from the statement. They should start with a # and a single space.
- Inline comments are unnecessary and in fact distracting if they state the obvious.

TODO: missing inline bit

---

# NEXT TIME ...

---

# Documentation Strings
# Version Bookkeeping
# Naming Conventions
# Overriding Principle
# Descriptive: Naming Styles
# Prescriptive: Naming Conventions
# Names to Avoid
# Package and Module Names
# Class Names
# Exception Names
# Global Variable Names
# Function Names
# Function and method arguments
# Method Names and Instance Variables
# Constants
# Designing for inheritance
# Public and internal interfaces
# Programming Recommendations

---

# References

[PEP8 guide](https://www.python.org/dev/peps/pep-0008)

[CAM Python style guide](https://docs.google.com/document/d/1aZoIyR9tz5rCWr2qJKuMTmKp2IzHlFjrCFrpDDHFypM/edit?usp=sharing)

TODO: pep8.org
TODO: https://medium.com/@drb/pep-8-beautiful-code-and-the-tyranny-of-guidelines-f96499f5ac17#.nl65ufnrm

---
# Joke break

When your boss tries to code

http://devopsreactions.tumblr.com/post/114659223515/when-your-boss-tries-to-code
