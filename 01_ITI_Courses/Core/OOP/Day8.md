## Inheritance

Search for => constructor and static members are inherited or not
* Child can inherit private members but cannot access them
* Protected member can be accessed inside class scope or inside the chain of inheritance

### Method overriding
* Without virtual keyword in parent, it's called method hiding
* Changes the behavior of a method in parent class in child class

``` cpp
class parent {
	int x;
	int y;
	int sum() {
		x + y;
	}
}

class child {
	int x;
	int y; 
	// method hiding but works
	int sum() {
		x + y + z;
	}
	
	// stack overflow, calls the child not the parent method
	int sum() {
		x + sum(); 
	}
	
	int sum() {
		x + parent::sum();
	}
}
```

``` cpp
class GeoShape() {
	protected:
	double dim1;
	double dim2;
	
	public:
	void SetDim1(double _dim1) {
	
	}
	void SetDim2(double _dim2) {
	
	}
	
	double GetDim1() {
	
	}
	
	double GetDim2() {
	
	}
	
	GeoShape() {
		dim1 = dim2 = 0;
	}
	
	GeoShape(double _dim1, double _dim2) {
		dim1 = _dim1;
		dim2 = _dim2;
	} 
	
	GeoShape(double _dim) {
		dim1 = dim2 = _dim;
	} 
	
	GeoShape(const GeoShape& other) {
	
	}
	
	virtual void Draw() {} ;
}
```

### Access modifiers
* Accesses modifiers are inherited as it is
* Private members are only inherited to the first child
* Protected members cannot be accessed in main

### Types of inheritance
#### Public (most used)
* Inherits all parent stuff with their access modifiers
* Cannot access private members still

#### Protected
* Protected and private are the same
* Public members are promoted to protected members

#### Private
* Private is not accessed at any level
* Protected is promoted to private (accessed only at this level)
* Public promoted to private (accessible)


=>delete calls destructor 
Point p1(2, 3) named object
Point(2, 3) annonymouse object, created and deleted at the same time


``` cpp
class Shape {
	protected:
	int myColor;
	
	public:
	//
	//
	
	Shape(int _myColor = 0) {
		myColor = _myColor;
	}
	Shape(const Shape& other) {
		myColor = other.myColor;
	}
	
	~Shape() {
	}
}

class Picture {
	MyLine *lPtr;
	int lSz;
	
	MyCircle *cPtr;
	int cSz;
	
	public:
	Picture() {
		lPtr = nullptr;
		cPtr = nullptr; 
		
		lSz = 0;
		cSz = 0;
	}
	
	void SetLines(MyLine*, _lPtr, int _lSz) {
		lPtr = _lPtr;
		lSz = _lSz;
	}
}

MyLine larr[3] = {MyLine(), MyLine(), MyLine()};
Picture p1;

// set relationship
p1.SetLines(larr, 3);

```