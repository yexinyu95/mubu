- (prerequisite)
  collapsed:: true
	- basic coding skills
	- familiar with computer system
	- mathematical maturity is helpful
- fundamental
	- overall
	  collapsed:: true
		- concept
		  collapsed:: true
			- finite, effective problem-solving method,
			- independent of special programming language,
		- usage
		  collapsed:: true
			- organize *huge amount* of data, and increase the running speed,
		- algorithm and data structure
		  collapsed:: true
			- algorithm is connected closely with data structure,
			- many data structures are byproduct or end products of algorithms,
			- encapsulate algorithms and data structure together,
	- [[java]]
	- coding method
	  collapsed:: true
		- language description
		  collapsed:: true
			- natural language
			- pseudo code
			- programming code
		- decompose into smaller subtasks
		- start from simple versions
		  collapsed:: true
			- low-level optimization effort could be most beneficial,
	- programming model
	  collapsed:: true
		- recursion
		  collapsed:: true
			- concept: a method can call itself,
			- keypoints
			  collapsed:: true
				- base case: always has a return
				- recursive case
				  collapsed:: true
					- always are smaller problems,
					- may have many cases,  while these cases should be disjoint,
				- it's easy to analyze recursion model's performance through mathematical tools,
		- object-oriented programming
		  collapsed:: true
			- data types
			  collapsed:: true
				- "data type" means a set of values and operations on these values,
				- most data types are built as a `class`, and using primitive data types,
				- these types often called "referenced types",
			- objects(instance)
			  collapsed:: true
				- three essential properties
				  id:: 6341453c-bef7-4b64-9dbc-cb7897e1689b
				  collapsed:: true
					- state : values stored in the instance,
					- identity : the name("identifier") of instance, sometimes called 'reference'; in hardware, it's similar to memory location,
					- behavior : operations,
			- build data types(class)
			  collapsed:: true
				- class inheritance
			- use data types
			  collapsed:: true
				- instance initialization(instantiate)
				  collapsed:: true
					- constructor
					  collapsed:: true
						- the basic method to create an instance often called "constructor",
						- constructor usually has no return value, and these methods are not `static` methods,
					- mechanism
					  collapsed:: true
						- allocate the memory
						- invokes the constructor
						- return a 'refenence' to the object,
					- new keyword
					  collapsed:: true
						- like other variables, ADTs needs declaration before initialize,
						- the initialization need to use `new` keyword,
						- these two steps can be combined, like `Counter heads = new Counter("heads");`
					- instance array
					  collapsed:: true
						- the elements of an array can be any type, including ADTs,
						- initializate an ADTs array is similar to ordinary arrays, including initialize the array, and initialize each instance (usually need use `for` loops),
						- `Counter[] rolls = new Counter[6]; for (int i = 1; i <= 5; i++) {rolls[i] = new Counter(i + "'s")};`,
				- instance alias
				  collapsed:: true
					- one instance could be assigned to a new name,
					- by comparsion, for basic data types, `int x = 2; int y= x;`will make y = 2,
					- while for ADTs, if x refer to an instance, the assignment `Counter y = x;` *will not* initialize a new instance y, y is just a "nick name" of the *same* instance x refer to,
					- so this "assignment" may cause errors,
				- object operations(APIs)
				  collapsed:: true
					- "abstruct" usually means the presentation of these data is hidden from the client,
					  collapsed:: true
						- which means when we use these ADTs, we only focus on the APIs, and we don't care the implementation of these API,
					- dot(period) method
					  collapsed:: true
						- ADTs can't be changed with basic operations, even they are made of basic data types; only APIs provided by ADTs can be used,
						- these APIs usually need to call with dot`.`, like `instance.method(argument);`,
						- these method are similar to ordinary static methods, they may change the value(but not return), print value, or return value,
				- object using
				  collapsed:: true
					- using as arguments
						- sometimes static methods may change the value of the object,
						- so make a copy of object's value, and use the value to compute is better,
					- using as return
						- java only allow one return "value",
						- while using objects as the return value is similar to has multiple return values,
		- modular programming
		  collapsed:: true
			- advantage
			  collapsed:: true
				- abstraction of lower-level methods can make program easier to understand as well as clearer,
				- people could use existing APIs from external libraries, so that they don't need to reproduce these basic methods,
				- "client - implementation" separation is important as well, for example, malware could use implementation code to find bugs and attack libraries,
			- APIs(application programming interfaces)
			  collapsed:: true
				- program which uses a method in another library often named as "client", and code to implement these written method always called "implementation",
			- modular ideas
			  collapsed:: true
				- it's important to treat every *own program* as a module and *try to reuse* them in the future,
				- APIs : write *presice note* about the function, include the function's usage, received data type and return type,
					- Java uses `/** note */` to mark function's notation,
				- testing : use some different examples to *test methods*' availability, through including `main()` function in module, and write the tests in the main function,
	- algorithm's performance
	  collapsed:: true
		- mathematical model
			- precise analysis may involve sophisticated mathematical computing, which is the main approach of  further class "analysis of algorithms",
-
-
-
- [[DataScience]]