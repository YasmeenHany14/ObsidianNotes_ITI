## Inheritance
* `Is a` relationship
* 
``` cpp
Assuming Base > Derived > Derived2;
and show is not overriden but hidden

Base* bPtr = new Dervied(3, 4);
bPtr -> show(); // im base

Base *bPtr2 = new Derived2();
bPtr2 -> show(); // im base

Derived *dPtr  = new Derived2();
bPtr2 -> show(); // im derived

```
* The previous behavior is not logically right, because it should look for the child class implementation before looking up the hierarchy
* This happened because show was hidden not overridden, compiler doesn't know there is a connection between the same function in different hierarchies, an with that it doesn't know the child class has an implementation for this function and doesn't look for it

#### How to apply late dynamic binding:
* Virtual and public method in the very parent class
* Child class should inherit from public
* Overridden function at child should be public
* Create a pointer from parent that points to child object 


## Abstract classes in cpp
* Class you cant create object from
* No abstract keyword, rather this class should have one pure virtual abstract function, the compiler prevents creation of objects of this class

``` cpp
class test {
	test () {}
	
	virtual void Helloo() = 0;// abstract flag
}
```

* If this function is not overridden in child classes, that means child classes are treated as abstract too

search => virtual destructor


## Template (Generics)
* Works in container data types (datatypes that holds objects inside it)
	Like stack, dict, ...
* Class can be template while struct cannot

```cpp
template<class T>
template<typename T>

stack<int>
```

## Overloading casting
* Overloading casting operators
* Return type can be omitted as it's obv the type we are overloading

``` cpp
int operator int() {

}

operator int() {

}
```

## Recursive functions
* Function calls itself
* Must have a base condition (break point) or it will result in stack overflow

``` cpp
long long pow(int base, int _pow) {
	if(pow == 0)
		return 1;
		
	return base pow(base, _pow - 1);
}
```
