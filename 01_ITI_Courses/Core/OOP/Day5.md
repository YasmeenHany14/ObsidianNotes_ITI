# OOP
* 4 OOP pillars
	1. Data hiding / Encapsulation
	2. Inheritance
	3. Polymorphism
	4. Abstractions
* Principle vs Concept vs framework
	* Principle is general knowledge
	* Concepte
	* Framework applies concept through programming language

### Encapsulation
* Hiding data by default and allowing specific ways to access part of the data
* Getters, setters and access modifiers

### Inheritance
* Base class giving it's props and methods to children

## Is cpp pure oop?
* No
	1. Standalone methods
	2. s

### Using namespace std
* Logical grouping for one or more data types with specific names to achieve performance and identity

``` cpp
class number {
	private:
	int real;
	int imagin;
	
	public:
	void SetReal(int _real) {
		real = _real;
		this -> real = _real;
		*(this).real = _real;

	void SetImagin(int _imagin) {
		imagin = _imagin;
	}
	
	int GetReal() const // saftey factor{
		return real;
	}
	
	int GetImagin() const{
		return Imagin;
	}
}

int main() {
	in
}
```