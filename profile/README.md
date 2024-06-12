# PythonicR: Bringing Python's Standard Library to R

## Overview

**PythonicR** is an organization dedicated to creating R packages that mirror the functionality and naming conventions of the Python standard library. We aim to ease developers' transition between Python and R by providing familiar functions and consistent naming conventions. With PythonicR, you can enjoy the power and flexibility of R without the cognitive load of remembering different function names and behaviors.

## Motivation

As developers, we often switch between programming languages, each with its unique syntax and naming conventions. Python's standard library is known for its simplicity and uniformity, making it easy to remember and use. However, R's powerful but diverse set of functions can sometimes be a hurdle for those accustomed to Python. **PythonicR** aims to bridge this gap by providing R packages that emulate Python's standard library, making it easier for Python developers to use R.

## Key Packages

### strs

[strs](https://github.com/pythonicr/strs) is an R package that provides string manipulation functions similar to Python's `str` methods. It offers a comprehensive set of tools for handling and processing strings in a Pythonic way.

### sets

[sets](https://github.com/pythonicr/sets) mimics Python's `set` data structure, offering functions for set operations such as union, intersection, difference, and symmetric difference.

### re

[re](https://github.com/pythonicr/re) brings Python's `re` module capabilities to R, enabling powerful and flexible regular expression operations.

### pathlib

[pathlib](https://github.com/pythonicr/pathlib) emulates Python's `pathlib` module, providing an object-oriented approach to handling and manipulating filesystem paths.

## Installation

You can install the PythonicR packages from our GitHub repository.

```r
# Install devtools if you haven't already
# install.packages("devtools")

# Install PythonicR packages
devtools::install_github("pythonicr/strs")
devtools::install_github("pythonicr/sets")
devtools::install_github("pythonicr/re")
devtools::install_github("pythonicr/pathlib")
```

## Getting Started

Under the hood, each package wraps a more mature R package. At most, a package will have two dependencies: the primary package it wraps and [checkmate](https://github.com/mllg/checkmate).

### String Manipulation

Both ``re`` and ``strs`` wrap functionality provided by [stringi](https://github.com/gagolews/stringi).

```r
library(strs)
library(re)

# Use strs functions similar to Python's str methods
print(strs_upper("hello world")) # "HELLO WORLD"
print(strs_upper(c("hello", "goodbye"))) # "HELLO" "GOODBYE"
print(strs_replace("hello world", "world", "R")) # "hello R"


# Use re functions similar to Python's re module
text <- "The quick brown fox jumps over the lazy dog"
match <- re_search("quick.*?fox", text)

# matches are always returned as a list of character vectors
print(match)
# [[1]]
# [1] "quick brown fox"
```

### Set Operations

Functions are based on functions available in [data.table](https://github.com/Rdatatable/data.table).

```r
library(sets)

# Use sets functions similar to Python's set methods
print(sets_union(c(1, 2, 3), c(4, 5, 6, 6)))          # c(1, 2, 3, 4, 5, 6)
print(sets_intersection(c(1, 2, 3), c(2, 3, 4)))      # c(2, 3)


# variadic arguments are supported
print(sets_intersection( # c(2, 3)
  c(1, 2, 3),
  c(2, 3, 4),
  c(4, 1, 5),
))
```

### Filesystem Paths with pathlib

This package wraps functions from the [fs package](https://github.com/r-lib/fs).

```r
library(pathlib)

Path_write_text("test.txt", "Hello, PythonicR!")
print(Path_read_text(path)) # "Hello, PythonicR!"
```

## Contributing

We welcome contributions to the PythonicR project. If you have suggestions, bug reports, or want to contribute code, please open an issue or submit a pull request on our GitHub repository.

## License

PythonicR packages are released under the MIT License. See the LICENSE file in each package's repository for more details.
