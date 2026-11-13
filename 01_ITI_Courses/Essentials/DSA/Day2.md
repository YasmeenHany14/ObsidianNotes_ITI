Operator perceeding
*  * / ^ have the same perceeding
* + - have the same
( ) >> * / ^ >> + -

* 2 cases
	1. Values => have no rules
	2. Operator 
		1. New op prio < op inside stack => push
		2. New op prio >= op inside stack => pop 1 element and 2 values, then push the op
		3. Empty stack => push


![[Pasted image 20261111095539.png]]