By Michael Mrozek

Local arrays are created on the stack, and have automatic storage duration -- you don't need to manually manage memory, but they get destroyed when the function they're in ends. They necessarily have a fixed size:
```c++
int foo[10];
```

Arrays created with operator new[] have dynamic storage duration and are stored on the heap (technically the "free store"). They can have any size, but you need to allocate and free them yourself since they're not part of the stack frame:
```c++
int* foo = new int[10];
delete[] foo;
```

[source](https://stackoverflow.com/questions/2672085/static-array-vs-dynamic-array-in-c)