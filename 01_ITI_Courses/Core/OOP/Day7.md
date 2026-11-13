## Shallow copy
* Copies created without calling constructor with bitwise copy
* If that copied object is the return value, that object is a temp anonymous object without a name
* This is the `c++` native behavior

### Enhancement for return value optimization (RVO)
* Instead of making a temp copy of the result, just pass the return value directly to it's destination
* This was done later as a constructor enhancement

### Shallow copy problems
 * Shallow copy happens for objects in stack, but what if that object carries an address for a dynamically allocated object
	 That copied object is destroyed and function EOL, and in return destroys that dynamically allocated array in the heap that is not copied, which corrupts the original object
* These problems are solved by passing by reference or creating a copy constructor

## Copy Constructor
* Called automatically when we create object in the following cases:
	1. Pass object by value
	2. Return object by value
	3. Assigning object to another one
* If copy constructor exists, bitwise copy wont happen, we should manually write complete logic there
* We can use reference if we wanna avoid going through copy ctor

``` cpp
class trial {
	int x;
	public:
	Trial(Trial& oldObj) {
		cout << "cpy ctor here\n";
	}
}

void TryMe(Trial param) {
	
}

Trial o1;
TryMe(param);

class Stack {
	int sz;
	int tos;
	int* arr;
	Stack(const Stack& old) {
		this->tos = old.tos;
		this->sz = old.sz;
		arr = new int[sz];
		for(int i = 0; i < tos; i++)
			this.arr[i] = old.arr[i];
	}
}

Stack s2(s1);
```

## Operator overloading
* Never return an object that will die at end of scope by reference

``` cpp
clasc Complex {
	int real;
	int img;
	Complex(int _real, int _img) {
		real = _real;
		img = _img;
	}
	
	// member
	// c1 + c2
	Complex operator+(const Complex& right) const {
		return Complex(this.real + right.real, this.img + right.img); // anonymous object
	}
	// c3 = c1 + 10 => caller is c1
	Complex operator+(const int num) const {
		return Complex(this.real + num, this.img);
	}
	
	// c3 = ++c1;
	// here we can pass return by reference, because object will still be alive after function ends, it doesn't belong to this scope
	Complex& operator++() const {
		++real;
		++img;
		return *this;
	}
	
	// c3 = c1++;
// this dummy param is used to differentiate between postfix & prefix overloadings
// compiler understands automatically the one with dummy is postfix
	Complex operator(int) const {
	// v1
		Complex result(real, img);
		real++;
		img++;
		return result;
		
	// v2;
		 Complex result2(*this)
	}
	
	// c3 += c1
	Complex operator += (const Complex& right) {
		real += right.real;
		img += right.img;
		return *this;
	}
	
	// c1 > c2
	bool operator > (const Complex& right) const {
		return this->real > right->real;
	}
	
	// c3 = c1 [useless to overload in this case]
	Complex& operator=(const Complex& right) {
		real = right.real;
		img = right.img;
		return *this;
	}
}
// standalone
Complex operator+(Complex left, Complex right) {
	// write result
}
Complex operator+(int num, const Complex& right) const {
	Complex result;
	// bla bla
	
}

Complex c1(3, 2);
Complex c2(3, 1);
Complex c3;
c3 = c1 + c2;
c3 = c1 + 10; // caller is c1
c3 = 10 + c1; // caller is 10, cannot write it in complex class => standlaone
c3 = c1++;
c3 = ++c1;
```

* Remember to delete caller array
* Copy ctor is used when we initialize new objects with existing values, while overload = operator when we copy existing values in existing objects.
``` cpp
// operator overloading in stack
class Stack {
	// c1 = c2 = c3;
	Stack& operator=(const Stack& stk) {
		delete[] arr;
		sz = stk.sz;
		tos = stk.tos;
		
		arr = new int[size];
		for(int i = 0; i< tos; i++)
			arr[i] = stk[i];
			
		return *this;
	} 
}

```

## Trace drawings in CPP
* Line needs 2 points
* Square or rectangle needs 2 points
* Triangle needs 3 points
* Circle needs 1 point and diameter
	setColor()
	rectangle()
	line()

``` cpp
class MyLine {
	private:
	point start; // composition
	point end;
	int myColor;
	
	public:
	void SetStart(point _start) {
		start = _start;
	}
	point getSStart() {
		return start;
	}
	void SetEnd(point _end) {
		end = _end;
	}
	point GetEnd() {
		return end;
	}
	void SetMyColor(int _myColor) {
		myColor = _myColor;
	}
	int GetMyColor() {
		return myColor;
	}
	// ctors
	MyLine() {
		myColor = 0;
	}
	MyLine(int x1, int y1, int x2, int y2, int _myColor) {
		start.SetX(x1);
		start.SetY(y1);
		end.SetX(x2);
		end.SetY(y2); // too many functions calls, 2 ctor + 4 sets
		// replace with contructor chaining

		myColor = _myColor;
	}
	
	MyLine(point _start, point _end, int _myColor) {
		start = _start;
		end = _end;
		myColor = _myColor;
	}
	
	// write copy ctor
	
	void Draw() {
		// use colors from graphics lib
		setColor(myColor);
		line(start.GetX(), start.GetY(), end.GetX(), end.GetY())
	}
}

MyLine l1;
// op:
// point ctor *2
// line ctor 
// line dest 
// point dest *2

MyLine l2(1, 2, 3, 4);
// op:
// same as the prev



```

* CTOR chaining
	calling other constructors inside another constructor and passing values to them
	better performance, making good use of the default constructor calls for outside objects inside the class
	Less code (DRY)

``` cpp
class Rect {
	private:
	Point upperLeft;
	Point lowerRight;
	int myColor;
	
	public:
	// setters and getters
	
	MyRect() {
		myColor = 0;	
	}
	
	MyRect(int x1, int y1, int x2, int y2, int _myColor)
	 : upperLeft(x1, y1), lowerRight(x2, y2) {
		myColor = _myColor;
	}
}
```


search for why prototype pattern is used in c# if passing is already by reference