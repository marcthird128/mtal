# MTAL Programming Language

MTAL is a low-level programming language that is very simple
to compile. It is basically a compact syntax for portable
assembly.

## Hello World

There isn't a standard function for output, but assuming `print`
exists and takes a single pointer argument, and that the pointer
size is 8 bytes, the program would be:

```
$str"H","e","l","l","o"," ","W","o","r","l","d",0
:main(str{print}
```

A method for data string literals has not been defined yet.

## Syntax

The official syntax is define in [GRAMMAR.peg](GRAMAR.peg).

## Operation

The function of the operators is defined in [OPERATION.md](OPERATION.md)

## Tutorial

The tutorial is in [TUTORIAL.md](TUTORIAL.md)

## Implementation

A C implementation for x86 is under `./impl`. Compile it with make.
