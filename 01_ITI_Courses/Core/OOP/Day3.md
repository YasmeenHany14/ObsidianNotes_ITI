# string functions
### reading and printing strings
``` cpp
char name[14+1];
cin>>name; //will stop at white space, cant read more than one word
cout<<name; //print till \0

#include <string.h>
gets(name); //not recommended
puts(name);
			//buffer overflow => self study
//enhancment
#include <stdio.h>

char name[15];
fgets(name,15,stdin)
fputs(name,stdout)

cin.getline(array of chars);
// need to use cin.ignore() before using it, incase of using cin before it to avoid having leftover chars in buffer being read
```

### More functions
* Functions inside `string.h` header
``` cpp
char c[10];
gets(c); // reads array of chars
puts(c); // prints array of chars

//strcpy(Larrayofcharacters,Rarrayofcharacters);
//strcat(Larrayofcharacters,Rarrayofcharacters);
//strcmp(Larrayofcharacters,Rarrayofcharacters); //ascii
//strcmpi(Larrayofcharacters,Rarrayofcharacters); //ascii
//strlen(Larrayofcharacters); //\0
//atoi(Larrayofcharacters);
//atof(Larrayofcharacters);
```

``` cpp
// strcpy
int main() {
	char fname[] = 'ali';
	char lname[] = 'ahmed';
	char fullname[30];
	fullname = fname; // compile error, fullname is just an address
	strcpy(fullname, fname); // copies from fname untill it reaches string terminator
	strcat(fullname, " ");
	strcat(fullname, lname);
	
//atoi(array of chars to int)
	char arr[10] = "22";
	int x = atoi(arr);
// atof(array to float)
	
}
```

# Structs

``` cpp
struct employee { // 12b 
	int id; // 4b
	int agel // 4b
	float salary; // 4b 
};

struct employee2 {
	char c; //1b
	int age; // 4b
	char s; // 1b
}

int main () {
	employee2 emp2;
	cout << sizeof(emp2); // will print 12
	// 1 + 3 padding + 4 int + 1 + 3 padding 
	// padding is added to make sure any allocation starts from an address divisable by 4, so each 1 is added 3 
}
```

# Pointers
* Variable carries address of another variable in memory of the same datatype
* `int *ptr = &x`
* `int *ptr;` => dangerous rubbish, it may contain address of something that is used in memory
	* Remember to assign ptr to variable address
``` cpp 
int main () {
	int x = 10;
	int* ptr = &x;
	ptr = &x;
	cout << *ptr; // prints 10
	cout << *x; // compile error
	
	float *ftpr = &x; // compile error - datatype missmatch
	ptr = x; // compile error
	*ptr = 1200; // ok
}
```
## Pointers size
* Depending on application type and operating system
* on 32-bit os or applications, pointer size is 4 bytes because it doesn't need more to hold the maximum range (32-bit os suuports up to 4gb ram only)
* 64-bit os and applications supports 16 ram+, more addresses which means more space needed to hold the address
	* size here is 8 bytes

## Arithmatic operations on pointers
``` cpp
int x = 10;
int * ptr = &x;
ptr++; // ptr moves 1 step in the size of its datatype(int)
		// ptr moves +4 addresses
ptr+1; // this does the same without changing value in memory
```

## General purpose pointer
* void pointer used for dynamic allocation
* used when i don't know what type i will allocate in runtime using malloc() in C
``` cpp
int main () {
	int x = 10;
	void *ptr;
	ptr = &x;
	cout << *ptr; // compile error, eompiler doesn't know how to print void
	cout << (int*) *ptr; // works (check astrics)
}
```

## Pointer to array
``` cpp 
int main() {
	int arr[10];
	int arr2[10];
	arr = &arr2; // 2 arrays pointing to the same location

	int *ptr;
	ptr = arr; // works
	ptr = &arr[0] // works
}
```
* Iterating over arrays using pointers
``` cpp 
int main() {
	int arr[5];
	int *ptr;
	ptr = arr;
	int val = 10;
	// v1
	for(int i = 0; i < 5; i++) {
		*ptr = val + i*10;
		ptr++;
	}
	ptr = arr; // dont forget to reset pointer
	
	// v2
	for(int i = 0; i  <5; i++) {
		*(ptr + i) = val + i*10; // no need to reset pointer
	}
	
	// v3
	for(int i = 0; i , 5; i++) {
		ptr[0] = val + i * 10; // whenever pointer points to array, it can be treated like an array and access it's value the same way we access
		// this is the recommended way
	}

}
```

## Pointers with strings/array of chars


## Pointer to pointer to int
``` cpp
int main() {
	int x = 10;
	int *ptr = &x;
	
	int* *ptr2 = &ptr; // variable have another variable address which have another variable address
	
	
}
```


## Pointer to struct

``` cpp
struct employee {
	int id;
	char name[10];
	int salary;
}

int main() {
	employee e1;
	employee *ptr = &e1;
	
	// v1
	strcpy((*ptr).name, "sara");
	(*ptr).age = 22;
	
	// v2, arrow syntax in pointer to struct
	ptr -> id = 1;
	ptr -> salary = 2000;
	strcpu(ptr -> name, "sara")
}
```

## Passing by reference
``` cpp
void swap(int* a, int* b) {
	int temp = *a;
	*a = *b;
	*b = temp;
}

int main() {
	int x, y;
	swap(&x, &y); // passed by reference	
}
```


### Passing array to function

``` cpp
void print
```


search how to pass 2d array

https://www.reddit.com/r/explainlikeimfive/comments/1rg4z8p/eli5_what_is_a_buffer_overflow_attack_and_how/
https://stackoverflow.com/questions/35810783/how-to-access-the-elements-in-a-2d-array-through-a-pointer
