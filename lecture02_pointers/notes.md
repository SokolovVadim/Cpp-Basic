# Pointers

## Genesis

0100b = 4d
value type -- values diapason

object type -- operations over object

Name is always related to a type -- statically typed language


Linear memory model.
Memory address type is pointer.

If address space is 22 then we need to have 5bit pointers (2^5 = 32).

`char` -- minimal addressable memory unit.
`sizeof(char) == 1` by default.

## Null pointer

0 - int

NULL - void*

nullptr - nullptr_t

Because of overload we need to use `nullptr`

`p[2] == *(p + 2) # move by 2*sizeof(p)`

## Lvalue references

```
int x;
int &y = x;
```

Binded ref can't be binded to another object

```
int x, y;
int &ref = x;
xref = y; // x = y
```

## Const reference

char& r1 = r; // ref to non const data
const char& r2 = r; // ref to const data


## Reference vs pointer

Reference can't be `nullptr`.
It's always valid. Can't use address arifmetics.

`this` is a ppointer.
There are no arguments why `this` is not a reference.

## Incapsulation in C++

Saves the invariant parts of the class, saves the visibility of the state.

## Invariants and linear memory model

Private and public gives access to the name of data.
We can cast class type to char* and change the consistency.
Just don't do it.

## References

Also saves the invariant. Can't call delete for the reference.


