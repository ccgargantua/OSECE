# Advanced C - Attributes (WIP)

In this text, the `__attribute__` feature of GCC-like compilers will
be covered. Note that not all attributes will be covered, just a small
subset. It is important to note that attributes are not a part of the
C standard and are extensions implemented by the compiler.

## What are attributes?

Attributes are characterstics that the developer can attach to
variables, functions, and structs. Attributes allow the programmer to
help the compiler tweak its behavior. These attributes are specified
by using the `__attribute__` keyword with the syntax
`__attribute__((ATTRIBUTE_NAME))`.

If that doesn't make much sense to you, don't worry. It is much easier to
understand when looking at examples, which we will do for the rest of this
lesson.

## Examples

### The `unused` attribute

The `unused` attribute is used to tell the compiler that there is a
*possibility* that a particular variable or function will not be used.

Consider the following code:

```c
#include <stdio.h>

int main(int argc, char** argv)
{
    printf("You supplied %d command line arguments.\n", argc - 1);
    return 0;
}
```

When compiled with the `-Wall` flag (which we know is good practice),
we get the following error:

```
src/main.c:3:27: warning: unused parameter ‘argv’ [-Wunused-parameter]
    3 | int main(int argc, char** argv)
```

Clearly we do not have a use for the `argv` in this program, but we
cannot exclude it from the parameter list. We can use the `unused`
attribute to tell the compiler (and anyone reading our code) that the
variable or method is intentionally unused, in this case `argv`.

```c
#include <stdio.h>

int main(int argc, char** argv __attribute__((unused)))
{
    printf("You supplied %d command line arguments.\n", argc - 1);
    return 0;
}
```

Now when we compile with `-Wall`, the program compiles without any
warnings.