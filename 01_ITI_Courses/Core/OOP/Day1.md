# Hardware
## Communication languages
* Hardware only understands:
	* Binary system
		* 0 - 1
		* The only way to communicate with hardware
* Octal - Hexadecimal 
	* Later translated to binary at the very last compilation step
	* Used to store large numbers in smaller symbols (chars + numbers)
	* To make it easier to translate and understand for humans
* Byte
	* 8 bit
	* 1024 byte => 1kbyte
	* 1024 kbite => 1mb
	* ...

## Some hardware parts

| HDD/SSD       | RAM       |
| ------------- | --------- |
| Non volatile  | colatile  |
| Bigger spaces | Smaller   |
| Cheaper       | Expensive |
| Slower (HDD)  | Faster    |
### Why use RAM and not SSD if they are both fast?
* RAM works as intermediate layer between hard disk and CPU
* It is much faster than even an SSD (nanoseconds vs. microseconds of latency), so the CPU doesn’t sit idle waiting for data.
* The CPU can access RAM directly, byte by byte, while storage is accessed in blocks through I/O controllers.
* RAM is volatile and has no write-wear limit, which suits temporary working data.
%%* It has some process, scheduling and communicates with the CPU???????? (maybe not correct)%%

### What happens when
* what happens if ram is completely full
	PC becomes completely unresponsive until it's hard reset

* what happens when CPU overloaded with instructions
	PC becomes slow, hot and fans loud noises
	If your fan is not working motherboard will get overheated


##  ASCII
* How symbols gets translated to the hardware
* Table of 7 bit character code and their respective value
* Translates numbers to symbols
* ASCII with unicode to determine which language the symbols belong to (to write in different languages)

### Extended ASCII 
* ASCII character set needed to be increased, with 2 ways
	1. Introducing extended ASCII, 8 bits instead of the default 7 bits 
		* Include the original 96 [ASCII](https://en.wikipedia.org/wiki/ASCII "ASCII") character set, plus up to 128 additional characters.
	2. The NULL sequence with null as the prefix
		* Expend the input from 1 to 2 bytes, the first byte is always NULL(0) which means the this instruction is a hardware/physical button that don't have a character (like arrows)
		* it combined existing standard ASCII characters (`0` through `127`) into temporary pairs to represent physical hardware actions (like moving a cursor or pressing `F1`
		* 0011 NULL => for example this is arrow right
	![[Pasted image 20261025201521.png]]

# Double - Long - Float comparison
==🔴SELF STUDY==
## Double - Float
* Double is a long float

| Float                                           | Double                                           |
| ----------------------------------------------- | ------------------------------------------------ |
| 32 bit                                          | 64 bit                                           |
| 1 sign bit + 8 exponent bits + 23 fraction bits | 1 sign bit + 11 exponent bits + 52 fraction bits |
| 7 digits precision                              | 15 digits precision                              |

## Int - Long
> For `long` and `int`, it comes from times, where standard integer was 16bit, where `long` was 32 bit integer - and it indeed _was_ longer than `int`

* Int is guaranteed to be at least 16 bits, could be from 16 to 32 depending on platform and implementation
* Long is guaranteed to be at least 32 bits

| Int             | Int    | Long   |
| --------------- | ------ | ------ |
| Size on windows | 32 bit | 32 bit |
| Size on mac-os  | 32 bit | 64 bit |
# Coding part
### Variable
* symbolic unique name, has a value and it's value can be changed

## Compilers vs Interpreters
when to use compiler and when interpreter and why? => ==🔴self study==


> [!NOTE]
> Difference between compilter and interpreter is in translation not execution
> 	Because of how the compiler reads the entire code together, then translates to native code
> 	Interpreter reads line and converts line by line, which makes something available to do with interpreters and not allowed with compiled code


## Standalone app and non standalone app
* application contains entry point (main) to tell the os where to start running this program from (.exe)
* non standalone application is any application without entry point (libraries to use for standalone applications) (.dll

## what happens when we run a cpp application
1. Compile code
2. linker (linking libs with code) 
	1. Dynamic and static linking
3. native code

## Error types
1. syntax error
2. runtime error (errors cause termination in tuntime)
3. linking error (header files missing or corrupted)
4. logical error (code not behaving as expected, but runs perfectely)

## Basic code/file structure in C++
1. Preprocessing phase
	# include libs
	# define => defining global aliases?
2. global declaration
	Global variable
	function
	struct/class
3. Entry point
	main()
		Local declaration
			Local vars or whatever inside the function
4. End of program
	Return 0, we return 0 if the program ran successfully without any errors
	Returning any other number means program wasn't successfull

## Notes
* To return logical address we use the &symbol (reference symbol)
* Forget break in switch statements is called => fall through

## do while and while
* do while => when the value of the variable used in the check condition is unknown( like waiting for using input )
* while => when the variable has a known value

# Lab
search turnany op
report on dynamic vs static linking
	=> what happens when we use iostream, in the linking phase does the whole file get linked or pnly what we used
	=> linking in run time and compile time