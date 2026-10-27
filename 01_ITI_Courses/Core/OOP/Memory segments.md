* When we execute our code, our memory during runtime is divided to 5 segments:

- [**Text Segment**: A text segment, also known as a code segment or simply as text, is one of the sections of a program in an object file or in memory, which contains executable instructions](https://www.geeksforgeeks.org/memory-layout-of-c-program/).
- **Initialized Data Segment**: Initialized data segment, usually called simply the Data Segment. [A data segment is a portion of the virtual address space of a program, which contains the global variables and static variables that are initialized by the programmer](https://www.geeksforgeeks.org/memory-layout-of-c-program/).
- [**Uninitialized Data Segment**: Uninitialized data segment often called the “bss” segment, named after an ancient assembler operator that stood for “block started by symbol.” Data in this segment is initialized by the kernel to arithmetic 0 before the program starts executing](https://www.geeksforgeeks.org/memory-layout-of-c-program/).
- [**Stack**: The stack area contains the program stack, a LIFO structure, typically located in the higher parts of memory](https://www.geeksforgeeks.org/memory-layout-of-c-program/).
- [**Heap**: The heap is often used to allocate big amounts of memory that are supposed to exist as long as the developer wants](https://www.geeksforgeeks.org/memory-layout-of-c-program/).

The most important two of them are stack and heap.

## Stack

- Stacks are used for static memory allocation.
- Allocation in stack happens on contiguous blocks of memory, and data are stored in the same order they came in.
- Stacks are faster to access that heap.
- Stack memory are less than that of heap.
- Stack is used to store (Function call stack)
    - Function call stack is the memory to be allocated whenever a function gets executed.
    - Each function call stack are separated from each other, but stored in the same order they came in, pop in the reverse order (FIFO).
    - Whenever a new function is called, all variables declared in it gets allocated in stack.
- When execution of a function is over, it’s function call stack gets de-allocated and any variable stored in it is no longer accessible.
- This kind of memory allocation is also known as Temporary memory allocation because as soon as the method finishes its execution all the data belonging to that method flushes out from the stack automatically.

## Heap

- Heap is used for dynamic memory allocation, memory allocated during runtime.
- Data stored in heap are not stored in the same order they came in.
- Whenever an object is dynamically created, it is created in heap space and the referencing information to these objects is always stored in Stack-memory.
- Heap memory allocation isn’t as safe as Stack memory allocation because the data stored in this space is accessible or visible to all threads.
- We have to worry about manually de-allocating any memory we manually allocated during runtime, normally it will not get deleted by itself even after the termination of the program.
- Heaps are slower than stack in access speed.
- Heap memory is larger than stack memory.

`<aside>  
💡 [A photo showing comparison between stack and heap](https://i.imgur.com/K1XVAzh.png)

![[Pasted image 20261026101100.png]]

illustration
</aside>`

## Value type and reference type

| **Value type**                                                             | **Reference type**                                |
| -------------------------------------------------------------------------- | ------------------------------------------------- |
| Stored in stack                                                            | identifier in stack and content in heap           |
| Memory limit for all data types stored in there (int goes up to 10^9 only) | No memory limit because heap is bigger than stack |
| ex) int, char, float, decimal, ..                                          | string, objects from classes                      |