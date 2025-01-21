# Scent of C++

1. The unification of data and methods

Not necessaty to define the method, declaration is enough

```
double Triangle::square() {
    // impl
}
```

In assembler we will see an ordinary label.
We don't see the address of `this`.
This is necessary in two stage name lookup

2. The generalization of data and methods

```
template<typename T> struct Point {T x, y;};
Point<int> pi;
Point<double> pd;
```

With `define` there are problems with generalizations

Std::sort works faster because of inline functions.
Problems of templates: compile time.
Modules and pre-compiled headers make it faster.

## STL

```
std::list<int> lst;
lst.push_back(2);
```

## Constructor

It's a function that creates an object, no return type.
