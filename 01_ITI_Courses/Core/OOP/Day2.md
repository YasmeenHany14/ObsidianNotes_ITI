function prototype
``` CPP
int func(int, int);
// or
int func(int left, int right)
```

``` cpp
// array length can be calculated as:
int main () {
	int arr[5];
	int arr_len = sizeof(arr) / sizeof(int); // there are other easier ways ofc
	int arr_len2 = arr.size();
	
	// arr itself is constant => the address of the first value of the array(base address)
	cout << arr // returns address 
	// setting default value for array
	int arr[10] = {0};
	arr1 = arr2 // compile error, we cant because each array has a CONSTANT address that cant be changed
	int arr[]; // compile error
	int arr[2] = {1, 2, 3, 4}; // compile error
	int arr[] = {1, 2, 3}; // works
	
	// wrong
	int arr[5];
	arr = {1, 2, 3, 4, 5};
	arr[0] = {1, 2, 3, 4, 5};
	// both wont work because the aray is a CONSTANT BASE ADDRESS OF THE first value
	// array default values only with array declaration
	
	// success but not standard
	// dynamic allocation using mingw
	int size;
	cin >> size;
	int arr[size];
	
}
```

==write about 2d array addressing in 4 bytes per location==
## Variables
[[Memory segments]]
### Local variable
* Declared inside a scope
* accessible in the same scope or scopes below
* life time: end of scope
* storage: stack

### Global variable
* Declared globally
* accessible in any scope
* life time: end of program
* storage: data segment
``` cpp
int x = 10;
int main() {
	int x = 30; 
	// this will work, as the global one is stored in the datasegment while the local one is stored in heap, no conflict happens 
	cout << x; // 30
	cout << ::x; // 10 => scope operator
}
```

### Static variable
* Declared only once in memory (considered a global variable in it's scope)
* accessible in the same scope or scopes below
* life time: end of program
* storage: data segment
``` cpp
int try() {
	static int x;
	x++;
	return x;
}

int main() {
	cout << try(); // 1 
	cout << try(); // 2
}

// static variables are initialized with it's type default value if not given one
```

## cin and ASCII values
* cin reads any printed character
``` cpp
int main() {
	char c;
	cin >> c;
	cout << "ascii is " << (int) c;
}
```
* But what if i want to print the ascii value for a non printable character like backspace
	* We use a library called

``` cpp
#include

int main() {
	char c;
	c = getch();
	// get any key from user at runtime printed or non printed
	// executes the moment we press the button, doesnt wait for enter
	cout << (int) c;
}
// problem is that it doesnt leave/write what character was pressed on the screen, so we know the ascii value but we dont know for which
int main() {
	char c;
	c = getche();
	// works exactly the same as getch except that it echos the printed key on screen
	cout << (int) c;
}
```
* A use case for getch and getche
``` cpp
int main () {
	int i = 0;
	char name[15];
	char c;

	cout << "enter ur name";
	while(c=getch() != 13)
		name[i++] = c;

	name[i] = `\0`;
	i = 0;
	while(name[i] != '\0')
		cout << name[i++];
		
	// OR a feature of cin that is execlusive to arrays of chars
	cin >> name; // does all whats before
	cout << name; // loops internally over the arr untill it finds '\0'
}
```
* gets, puts, cin, cout
* cin doesn't detect spaces, and considers it end of string, cant write full names
* while gets records every character including spaces until enter is pressed
``` cpp
int main () {
	char name = [15];
	gets(name); // have some better alternatives because is casuses buffer overflow
	puts(name);

}
```

## String.h

``` cpp
int main () {
	char name[15] = {'a', 'l', 'i', '/0'};
	// same as
	char name[15] = "ali";
	cout<< strlen(name); // returns string length until if finds the \0 not the actuall reserved size
}
```

## Struct
* Must be upper case + singular
* variables are lower case or start with underscore , camel case if consists of 2 words


## lab
