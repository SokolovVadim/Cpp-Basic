# Names

## Dynamic memory allocation

```
new
new[]
```

If we call delete[] instead of delete it will cause UB.
There is a counter of memory blocks allocated in the beginning of the allocated memory

## Scope

Sections in program, where we can access the variable.

## Lifetime

All time periods when the variable is valid.
Right after initialization.

`int a = a; // UB`

Declared but lifetime didn't start.

## Dangling pointer

A pointer pointing to the variable with expired lifetime.

Dangling reference.

1.
```
int *p = new int[5];
int &x = p[3];
delete [] p;
x += 1; // UB
```
2. return reference to a local variable.

## Cdecl

```

(&c) // ref

(&c)[10] // ref on array

(*(&c)[10]) // ref on array of 10 pointers

(*(&c)[10])(int ) // ref on array of 10 pointers on function

(*(&c)[10])(int *&) // ref on array of 10 pointers on function taking the reference on a pointer

char *(*(&c)[10])(int *&); // ref on array of 10 pointers on function taking the reference on a pointer and returning a pointer to char

```

## Alternative to typedef: using

using ptr_to_fref = void (*) (int&);

You can use it with templates.


## Mangling

C gives strong name garantees.

And it doesn't allow overload, templates.

C++ is C and mangling with other additional capabilities.

## Extern "C"

`struct S {exter "C" void foo();};`

Can't do this because it's in the structure. It's mangled in the calling block, so can't extern from there.

## Overload and Name Resolution

```
float sqrt(float x);
double sqrt(double x);

sqrt(42); // can't understand what to call
```

Name resolution. What is it gonna call?
Compilation error.
From int there is one implicite cast from float and double.

## Rules for the Name Resolution

1. Exact match: `int->int, int -> const int&`
2. Exact match with a template: `int -> T`
3. Standard transformation: `int->char, float->unsigned short`
4. User's transformations: for user's classes
5. Variable number of arguments: `foo(...)` -- is not used often
6. Incorrectly binded links: `literal->int&`

Viable candidates -- all possibly resolvable names.

## Constructor overload

Nice to use with constructors

## Namespaces

All names belong to some namespaces.

```
int x;
int foo() {
    return ::x; // global namespace
}

```

## STD namespace

1. All from standart library belongs to std::.
2. Exceptions only old libs like <stdlib.h>.
3. To include atoi in std:: was made <cstdlib.h>
4. Can't add my names to std::
5. Can't start my names from _ or Upper case.

## Our namespaces

Structs also make namespaces.

```
namespace Containers {
    struct List {
        struct Node;
    };
}
```

`Containers::List::Node n;`

Namespaces can be reopened with additional info.

## Directive using

```
using std::vector;
using namespace X; // bad because opens it to a global space
```

## Anonymous namespaces

Substitutes static functions.

```
namespace {
int foo() {
    return 100;
}
}

int bar() { return foo(); }
```

It looks like that after compilation.


```
namespace hskvrjn1 {
int foo() {
    return 100;
}
}

using namespace hskvrjn1;
int bar() { return foo(); }
```

1. Make a namespace with a complex unique name
2. Use it immediately

## Rules for namespaces

1. Don't abuse global namespace
2. Never write using namespace in headers
3. Use anonymous namespaces instead of static functions
4. Don't use anonymous namespaces in headers

## The right Hello, World!

```
#include <iostream>
namespace {
    const char* const helloworld = "Hello, world!";
}

int main() {
    std::cout << helloworld << std::endl;
}

```

main() is always visible in global namespace, from C-API so the OS can call it.







