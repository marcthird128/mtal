# MTAL Programming Language

MTAL is a low-level programming language that is very simple
to compile. It is basically a compact syntax for portable
assembly.

## Hello World

There isn't a standard function for output, but assuming `print`
exists and takes a single pointer argument, and that the pointer
size is 8 bytes, the program would be:

```
#12s"Hello World",0u1 -- Define string
)8s}print{ -- Call print
```

The most compact form is `#12s"Hello World",0u1)8s}print{` with no
extra space or comments.

## Syntax

