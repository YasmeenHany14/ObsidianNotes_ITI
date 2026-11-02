# Dynamic allocation

## Array of addresses
``` cpp
int *ptrarr[4];
int a = 4;
int arr[4];

ptrarr = a; // False, cant equal 2 constant addresses
ptrarr = &a; // False, cant equal 2 constant addresses
ptrarr[0] = a; // False, a is a value not an address
ptrarr[0] = &a; // works

ptrarr[0] = arr; // works
ptrarr[0] = &arr; // works in c, and compile error in c++

*ptrarr = arr; // works, *ptrarr is the value of the base address not the constant address

```

## Casting
* Convert value/state from data type to another data type
* Depends on state and value
* Have 2 types
	1. Implicitly => compiler will do it itself
		Like converting from float to int
	2. Explicitly => developer will do it

``` cpp
int main () {
	int x = 22; // 4b
	double y = 33; // 8b
	y = x; // implicit casting
	y = (double) x; // explicit casting, wont work if y reserved space is less than x value
	// unsafe casting, risking overflow, explicite casting is a must here
	x = int(y); 
	cout << "x = " << x;
	cout << "y = " << y;
}
```

### Promotion
``` cpp
int x = 4;
char c = 'M';
// promotion
// c got implicitly casted to int, converted to it's ASCII value
int result = x + c;
result = x + (int)c; // casting here is useless

//------------------------------------------------
int x = 4, y = 9;
float z;
z = x/y; // zero, int division leaves no ksor
// explicit casting is must here
z = (float) x / y; // 0.75

```

### GP Pointer Casting
* Explicit casting is a must
``` cpp
int x = 10;
void *ptr;
ptr = &x;

cout << *ptr; // wont work, cant print void
int *tmpPtr = (int*)ptr;
cout << *tmpPtr; // 10, works because of castig to int, and compiler knows how to print int

// or
cout << *((int*) ptr); // 10
```

## Dynamic allocation
* Array resizing is impossible after declaration, fixed size
	Cannot be modified or deleted until end of scope
* Allocating and deallocating in runtime
* Dynamic allocation is done in heap
* Use the `new` keyword
``` cpp
// to allocate 5 ints and return the address of tje first element created
int* ptr = new int[5]; // pointer to int
char* ptr = new char[]; // pointer to char and so on
```
* OS deals with cleaning the stack, devs deals with cleaning heap to avoid memory leaks

``` cpp
int size;
cin >> size;
int* ptr2 = new int[size];
```

// rewatch dynamic allocation 9:24
### Looping through dynamic allocated array


### Allocating chars
``` cpp
int _size = 15;
char *cptr = new char[15];
*(cptr + 0) = 'A';
// and so on
// or
cptr[0] = 'A';
// better than manually writing every word:
cin >> cptr;
cout << cptr;

gets(cptr);
puts(cptr);

fgets(cptr, 15, stdin);
fputd(cptr, stdout);

cin.getline(cptr, 15);
```

### Deallocation
* On dynamic allocation, OS casts protection on the reserved space in heap, so to deallocate we need to remove the protection first
* `delete [] address of first element allocated`
* After deallocating ptr still reserving it's value, but becomes an undefined address
``` cpp
int* ptr = new int[5];
delete[] ptr; // removes protection on enitre array

delete ptr; // removes the protection on the base address ONLY
// used with non array objects

```

### Function to pointer
// rewatch 10:21

### Dynamic allocation for array of pointers
* Dynamically allocating 2d array
``` cpp
int col = 4;
int *ptr[3];

ptr[0] = new int[col];
ptr[1] = new int[col];
ptr[2] = new int[col];
ptr[3] = new int[col];
// from this moment, int*ptr[3] became int ptr[3][4]

# Deallocation
delete[] ptr[0];
delete[] ptr[1];
delete[] ptr[2];
delete[] ptr[3];
```
![[Pasted image 20261029102747.png|390]]


#### Dynamically allocating rows and cols
``` cpp
int arr[3][4];
int row = 3, col = 4;
int* *ptr = new int*[row];
// from this moment, int ** ptr === int* ptr[3]

for(int i = 0; i < row; i++)
	ptr[i] = new int[col];

// deallocating
delete[] ptr;
for(int i = 0; i < row; i++)
	delete[] ptr[i];
// deletes the protection only from rows addresses
// deleting them first puts us in a race condition to deallocate the rows values before thier base of overwritten

```

## Pointer to array of struct
``` cpp
struct Employee {
	int id;
	int age;
	char name[10];
}

int sz = 3;
Employee *empPtr = new Employee[sz];
delete[] empPtr;

```

### Modern CPP dynamic allocation default value
* Setting default values for dynamically allocated array
* wasn't possible in c, or older `c++`
``` cpp
int *ptr = new int[5] {1, 2, 3, 4, 5};
int *ptr = new int[5] {};
int *ptr = new int[5] ();
