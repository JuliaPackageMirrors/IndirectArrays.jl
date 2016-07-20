# IndirectArrays

[![Build Status](https://travis-ci.org/timholy/IndirectArrays.jl.svg?branch=master)](https://travis-ci.org/timholy/IndirectArrays.jl)

[![Coverage Status](https://coveralls.io/repos/timholy/IndirectArrays.jl/badge.svg?branch=master&service=github)](https://coveralls.io/github/timholy/IndirectArrays.jl?branch=master)

[![codecov.io](http://codecov.io/github/timholy/IndirectArrays.jl/coverage.svg?branch=master)](http://codecov.io/github/timholy/IndirectArrays.jl?branch=master)

An `IndirectArray` is one that encodes values using a combination of
an `index` and a `value` table: concretely, if `A` is an
`IndirectArray`, then `A[i,j...] = value[index[i,j,...]]`.

`IndirectArrays` can be used to represent
[indexed images](https://en.wikipedia.org/wiki/Indexed_color),
sometimes called "colormap images" or "paletted images."

## Installation

```jl
Pkg.add("IndirectArrays")
```

## Usage

For example:

```
using IndirectArrays, Colors

colors = distinguishable_colors(20)
index = rand(1:20, 256, 256)
A = IndirectArray(index, colors)
```

The value array can be of any type, it does not have to be color information.

Note that `setindex!` is not supported: you cannot set the value of
`A` to an arbitrary value, because the value has to be one of the values in the value table.