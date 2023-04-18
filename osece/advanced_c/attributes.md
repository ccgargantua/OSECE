# Advanced C - Attributes (WIP)

In this text, the `__attribute__` feature of GCC-like compilers will
be covered. Note that not all attributes will be covered, just a small
subset. It is important to note that attributes are not a part of the
C standard and are extensions implemented by the compiler.

Attributes covered in this text:

* `unused`
* `deprecated`
* `nonstring`

## What are attributes?

Attributes are characterstics that the developer can attach to
variables, functions, and structs. Attributes allow the programmer to
help the compiler tweak its behavior. These attributes are specified
by using the `__attribute__` keyword with the syntax
`__attribute__((ATTRIBUTE_NAME))`.

If that doesn't make much sense to you, don't worry. It is much easier to
understand when looking at examples, which we will do for the rest of this
lesson.

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

### The `deprecated` attribute

The `deprecated` attribute is used to mark a variable or function as
deprecated, and the compiler will generate a warning when it encounters
code that usese that variable or function.

Consider the following code:

```c
#include <stdio.h>

int __attribute__((deprecated)) deprecated_add(int x, int y)
{
    return x + y;
}

int main(void)
{
    printf("%d\n", deprecated_add(2, 2));
    return 0;
}
```

If we compile this code, it will run, but the following warning will be
generated.

```
src/main.c:10:5: warning: ‘deprecated_add’ is deprecated [-Wdeprecated-declarations]
   10 |     printf("%d\n", deprecated_add(2, 2));
      |     ^~~~~~
src/main.c:3:33: note: declared here
    3 | int __attribute__((deprecated)) deprecated_add(int x, int y)
      |
```

It is worth mentioning that some attributes take arguments, sometimes these
arguments can even be optional. `deprecated` is one such attribute. You may
see something like `__attribute__((deprecated ("Please use <other_function> instead")))`.
This will tack the message to the end of the error.

### The `nonstring` attribute

The `nonstring` attribute marks character arrays and pointers, both signed and unsigned,
as potentially not ending with a null-terminator. Upon passing a variable with such
an attribute to a function that assumes its parameter to be null-terminated, the
compiler will spit out a warning. Consider the following code:

```c
#include <stdio.h>

int main(void)
{
    char thing[] __attribute__((nonstring)) = "";
    printf("%s\n", thing);
    return 0;
}
```

If we compile this code, it will run, but the following warning will be
generated.

```
src/main.c:8:5: warning: ‘__builtin_puts’ argument 1 declared attribute ‘nonstring’ [-Wstringop-overread]
    8 |     printf("%s\n", thing);
      |     ^~~~~~~~~~~~~~~~~~~~~
src/main.c:6:10: note: argument ‘thing’ declared here
    6 |     char thing[] __attribute__((nonstring)) = "";
      |          ^~~~~

```