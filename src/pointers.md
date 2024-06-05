# Pointers

A pointer is simply a variable that holds the location in memory where a value is stored

the `&` is the address operator. 
It precedes a value type and returns the address of the 
memory location where the value is stored

```go
    x := "hello"
    pointerToX := &x
```

the `*` is the indirection operator. 
It precedes a variable of pointer type and returns the pointer-to value.
This is called `Dereferencing`

```go
    x := 10
    pointerToX := &x
    fmt.Println(pointerToX) // prints the memory address
    fmt.Println(*pointerToX) // prints 10
```

A `pointer type` is a type that represents a pointer.

The built-in function `new` creates a pointer variable.
the `new` function is rarely used.

For structs, we can use the `&` operator before the struct literal.
Cannot use `&` for a primitive type and constants

Go gives you the choice to use `pointers` or `values` for both primitives and structs.
Most of the time, you should use a `value`.

A secondary benefit is that using values reduces the amount of work that the garbage
collector has to do.

Since Go is a `call by value` language, the values passed to functions are copies. For non-pointer types
like primitives, structs and arrays, this means that the called function cannot modify the original.

However, if a pointer is passed to a function, the function gets a copy of the pointers.
Which means the original data can be modified by the called function.

#### First Implication

When you pass a nil pointer to a function, you cannot make the value non-nil.
You can only reassign the value if there was a value already assigned to the pointer.

#### Second Implication

If you want the value assigned to a pointer parameter to still be there when you exit the function,
you must dereference the pointer and set the value.
Dereferencing puts the new value in the memory location pointed to by both the original and the copy.

### Pointer Passing Performance

If a struct is large enough, there are performance improvements from using a pointer to the struct
as either an input parameter or a return value.





