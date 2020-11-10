By Manu343726

Memory allocated at compile-time means the compiler resolves at compile-time where certain things will be allocated inside the process memory map.

For example, consider a global array:
```c++
int array[100];
```

[source](https://stackoverflow.com/questions/21350478/what-does-memory-allocated-at-compile-time-really-mean)

The compiler knows at compile-time the size of the array and the size of an int, so it knows the entire size of the array at compile-time. Also a global variable has static storage duration by default: it is allocated in the static memory area of the process memory space (.data/.bss section). Given that information, the compiler decides during compilation in what address of that static memory area the array will be.

Of course that memory addresses are virtual addresses. The program assumes that it has its own entire memory space (From 0x00000000 to 0xFFFFFFFF for example). That's why the compiler could do assumptions like "Okay, the array will be at address 0x00A33211". At runtime that addresses are translated to real/hardware addresses by the MMU and OS.