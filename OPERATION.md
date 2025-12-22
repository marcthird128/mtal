# Operation

Each operator's arguments and function is defined below. `<argument>` names an
argument. `<argument:size>` indicates that all arguments with the same size name
are of the same size (e.g. `<a:T>` and `<b:T>` must be the same size). `...`
indicates that the argument is a comma-seperated list. For more details on an
operator's syntax, see [GRAMMAR.peg](GRAMMAR.peg).


## Expressions

The description is preceded by the size of the output inside `[]`.

- `' <sz> <expr>`: [`sz`] Dereferences `expr`
- `. <sz> <expr>`: [`sz`] Truncates or zero-extends `expr` to `sz` bytes
- <code>&#96; &lt;sz> &lt;expr></code>: [`sz`] Truncates or sign-extends `expr`
  to `sz` bytes
- `+ <a:T> <b:T>`: [`T`] Adds `a` and `b`
- `- <a:T> <b:T>`: [`T`] Subtracts `b` from `a`
- `* <a:T> <b:T>`: [`T`] Multiplies `a` and `b`
- `/ <a:T> <b:T>`: [`T`] Divides `a` by `b`
- `% <a:T> <b>`: [`T`] Division remainder of `a` / `b`
- `& <a:T> <b:T>`: [`T`] Performs bitwise AND on `a` and `b`
- `| <a:T> <b:T>`: [`T`] Performs bitwise OR on `a` and `b`
- `^ <a:T> <b:T>`: [`T`] Performs bitwise XOR on `a` and `b`
- `~ <a:T>`: [`T`] Performs bitwise NOT on `a`
- `<< <a:T> <b>`: [`T`] Shifts `a` `b` bits to the left
- `>> <a:T> <b>`: [`T`] Shifts `a` `b` bits to the right and zero-extends
- `>>> <a:T> <b>`: [`T`] Shifts `a` `b` bits to the right and sign-extends
- `! <a:T>`: [`T`] Returns 1 if `a` is 0, returns 0 otherwise
- `== <a:T> <b:T>`: [`T`] Returns 1 if `a` equals `b`, returns 0 otherwise
- `< <a:T> <b:T>`: [`T`] Returns the sign bit of a-b
- `> <a:T> <b:T>`: [`T`] Returns the sign bit of b-a

## Statements

- `$ <label> <data>...`: Defines `label`, which points to the start of
  a contingous block of all the `data` arguments
- `[ <sz> <name>...`: Defines variable(s) `name` of size `sz`
- `] <name>...`: Deletes variable(s) `name` so they can be defined elsewhere
- `( <value>...`: Puts the `value`(s) into function storage
- `) <sz><dest>...`: For each `sz` and `dest` pair, takes contingous values 
  of size `sz` from function storage and puts them into `dest`.
- `= <dest> <value>`: Puts `value` in `dest`.
- `: <name>`: Defines a label - `name` now points to the code after it
- `; <name>`: Deletes label `name` so it can be defined elsewhere
- `{ <target>`: Calls target by saving the pointer to the code after in a way
  that makes recursive calls possible
- `}`: Returns to the last saved pointer from a call
- `? <condition> <target>` Jumps to `target` if `condition` is non-zero
