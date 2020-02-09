# ArrayOps

ArrayOps is my old library from 2006 for performing vector computations in C++. It is conceptually similar to the valarray-class of the Standard Template Library (STL). However, ArrayOps employs socalled [Template Meta-Programming](http://en.wikipedia.org/wiki/Template_metaprogramming) along with other advanced object-oriented programming techniques to improve efficiency and flexibility. ArrayOps essentially provides syntactic sugar for vector-notation which automatically compiles into a single flattened loop for each assignment involving vector expressions.

ArrayOps had a number of advantages over similar libraries from that time (e.g. Blitz++ and POOMA), including a much simpler framework that easens the maintenance and user-specialization, which means ArrayOps also provides different vector-datatypes that are tailored to specific needs, and all vector-datatypes may be combined arbitrarily in arithmetic expressions.


## Example

To illustrate the basic idea of ArrayOps, consider the following C++ source-code example where we create and manipulate three arrays, each containing 100 elements:

    const unsigned int k = 100;
    ArrayOps::Array<double> A(k), B(k), C(k);
    double b, c;

    // Read numbers b and c from somewhere ...
    // Read arrays B and C from somewhere ...

    A = b*B + c*C;

Here, due to the use of socalled meta-programming, the last line is automatically transformed at compile-time into the following loop:

    for (unsigned int i=0; i<A.Size(); i++)
    {
        A[i] = b*B[i] + c*C[i];
    }

Where the datatypes are ensured to be the same at compile-time and the sizes of the arrays are asserted to match in debug-mode. Note that no implicit allocations of socalled temporaries take place as would be the case if the valarray-class from the STL had been used.


## Download

- [PDF manual](https://github.com/Hvass-Labs/ArrayOps/raw/master/ArrayOps2_0.pdf)
- [ZIP source-code](https://github.com/Hvass-Labs/ArrayOps/raw/master/ArrayOps2_0.zip)
- [ZIP test-program](https://github.com/Hvass-Labs/ArrayOps/raw/master/ArrayOpsTest2_0.zip)


## Installation

Installing and using ArrayOps is incredibly simple, as there are no code-libraries that have to be compiled, and ArrayOps only consists of C++ header-files. Simply do the following:

1. Download the ArrayOps source-code (see above).
2. Unpack the ArrayOps source-code to a directory of your choice.
3. Add that directory to the include-paths of your C++ project.
4. Add `#include` statements to your source-code, for the ArrayOps datatypes that you need (e.g. `Array`, `ArrayMini`, or `ArrayUse`).
5. Write your source-code using ArrayOps, and compile.

## Compatibility

ArrayOps was developed in MS Visual C++ 2005. It is unknown whether it still works at the time of this writing in the year 2020.

The parallel features may be disabled during compilation, either by switching off OpenMP support in the C++ compiler, or by forcing all arrays to be non-parallel.
