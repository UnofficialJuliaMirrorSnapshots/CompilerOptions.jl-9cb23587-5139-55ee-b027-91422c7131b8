# CompilerOptions

[![Build Status](https://travis-ci.org/sjkelly/CompilerOptions.jl.svg?branch=master)](https://travis-ci.org/sjkelly/CompilerOptions.jl)
[![Coverage Status](https://img.shields.io/coveralls/sjkelly/CompilerOptions.jl.svg)](https://coveralls.io/r/sjkelly/CompilerOptions.jl?branch=master)

This is a basic package for providing introsepction into Julia's compiler
options. This functionality is now part of Base in 0.4, so this package aims
provide a consistent API between 0.3 and 0.4.

## Use

### Julia 0.3

CompilerOptions defines the following for Julia 0.3:

```
    immutable JLOptions
        build_path::Ptr{Cchar}
        cpu_target::Ptr{Cchar}
        code_coverage::Int8
        malloc_log::Int8
        check_bounds::Int8
        int_literals::Cint
    end

    JLOptions() = unsafe_load(cglobal(:jl_compileropts, JLOptions))
```

For example, it is now possible to see if Julia is being run with code-coverage
enabled:

`JLOptions().code_coverage`

### Julia 0.4

Julia 0.4 provides the same type, but is unexported. This package simply
provides an alias for the function in Base:

`JLOptions() = Base.JLOptions()`

## Credit
This package was kick started with the help of ihnorton, jakebolewski, and staticfloat.

* https://gist.github.com/staticfloat/93d7050a08ff7bb52373
* https://groups.google.com/d/msg/julia-users/TkYi6CJrSVE/L-ydZ67ujiUJ

## License
Available under the [MIT "Expat" License](http://en.wikipedia.org/wiki/MIT_License). See: [LICENSE.md](./LICENSE.md).

