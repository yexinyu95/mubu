- (prerequisite)
	- Get Started with C++ in Visual Studio Code，
- ## C++ program
	- ### Compiler Tool Chain
	- preprocessor
	  background-color:: #49767b
		- include libraries' file and "translate" code with libraries,
	- compiler
	  background-color:: #49767b
		- generate a object file,
	-
	- ### compile files
	- need to use `g++` (instead of `gcc`)to compile cpp files, while `make file.cpp` are still available，
	- use `g++ file.cpp -o file`to change execution file's name to `file`，
	- use `g++ -S file.cpp`to make a compile code file，
	-
	- ### separate compilation
	- split program into several files,
	- first compile to "object code", `g++ file.cpp -c`,
	- then combine multi object files and compile them to execution file, `g++ file1.o file2.o -o file`
- ## Basic Syntax
	- need to use `;` as a notation of one statement ends,
	- comment pairs `/* */` cannot nest, which means `/* com /*comment */  ment*/` will cause error,
	- `//comment` is also available,
	- statically typed language, each object has a predefined data type and cannot change,
	- case-sensitive(upper- and lowercase letters are distinct),
- ## Data types
	- ### literal value
	- 1. integer literal
	- can contain any number of single quotes (') for readability, like `100'000'000`,
	- can have suffixes to specify its type (suffixes are case *in*sensitive), like`123456L`,
	-
	- 2. float literal
	- can have suffixes to specify its type (suffixes are case *in*sensitive), like`123.456L`,
	- can use scientific notation, like `3e1 == 30`, `3e-1 == 0.3`(no spaces),
	-
	- 3. character literal
	- escape sequences
	  background-color:: #49767b
	- use backslash to print some special chars,
	- not printable characters
	  background-color:: #49767b
	- which means these char has no visible image, like backspace, control,
	- while some of these char can be used with backslash, like`\b` mean backspace,
	- use ASCII codes
	  background-color:: #49767b
	- like `\115`(octal, not decimal) and `\x4d`(hexadecimal without 0) represents 'M',
	-
	- ### primitive types
	- 1. integer
	- unsigned integer
	  background-color:: #49767b
	- interger's size
	  background-color:: #49767b
	- `<cstdint>`defines precise integers like `int64_t`,
	- number base
	  background-color:: #49767b
	- a literal number written in decimal, octal(prefix 0), or hexadecimal(prefix 0x) is all vaild,
	- `int i = 20;`,`int i = 024;`, `int i = 0x14;`has same meaning,
	- C++ doesn't support binary integers,
	-
	- 2. `size_t`
	- like a integer, and usually identical to an unsigned long,
	-
	- 3. float
	- `float`, `double`, and `long double`
	- double is commonly used nowadays,  as float usually does not have enough precision,
	- IEEE 754 floating point standard,
	-
	- 4. characters
	- `char` is always 1 byte, and used with basic character set(like ASCII),
	- `char16_t` and other type are designed for extended character sets(like Unicode, UTF-16),
	- but *printing* Unicode to the console is complicated and cannot just use `printf`, `putchar` or `std::cout`,
	- (unsigned char)
	-
	- 5. Boolean
	- `bool test = true;`
	-
	- 6. `std::byte`@
	- available in `<cstddef>` library,
	- use with bitwise operators to work with raw memory,
	-
	- 7. void@
	-
	- ### type conversion
	- 1. implicit conversion
	- integral promotion
	  background-color:: #49767b
	- most times, variables have integer value but smaller than `int`(such as `bool`, `char`, `short`) will be converted to `int` type,
	- precision promotion
	  background-color:: #49767b
	- in expressions mixed `int` type and `float` type, the `int` variable will be promoted to `float` and calculate with another variable,
	- initialization
	  background-color:: #49767b
	- in initialization(and assignment), the "rvalue" will be converted to the left variable's type,
	- truncation
	  background-color:: #49767b
	- like `int i = 3 + 3.14;`, for `3 + 3.14`, 3 will be promoted to `3.0` and the answer will be `6.14`,
	- but the initialization type is `int`, so the result will be truncated to 6; and that will lead to precision loss,
	- use`auto i = 3 + 3.14;` will show the promotion(i's type will be `double`),
	- bool conversion
	  background-color:: #49767b
	- in conditions, non-bool expressions are converted to bool,
	- class-type defined conversion@
	  background-color:: #49767b
	- unsigned types
	  background-color:: #49767b
	- assign an out-of-range value to an object of signed type, the result is undefined,
	-
	- 2. explicit conversion(cast)
	- cast is not recommended to use, it's better to find alternative way to avoid using cast,
	-
	- precision promotion
	  background-color:: #49767b
	- `static_cast` is most commonly used, like `static_cast <double> j`;
	- @`const_cast` can apply for(and only for) const modifiers,
	  collapsed:: true
		- often used to change a non-const variable through const modifiers,
	- @retrieve pointer value
	  collapsed:: true
		- value stored in void pointer can be retrieved by casting the void pointer to corresponding type's pointer,
	- @reinterpret_cast
	-
	-
	- ### abstract data types
	- 1. string
	- concept
	  collapsed:: true
		- a sequence of characters,
		- C++ defined built-in `string` datatype,
	- initialization
	  collapsed:: true
		- like other primitive types, `string str;` define a string `str` and give it a default value `""`,
		- by convention, words embraced by `""`will be treated as a string, like`string str = "cpp";`,
		- multi-line string : string literals *only separated* by blank(space, enter) will be add to one, like `"app"    "cpp" == "appcpp"`, that will enhance the readability for long sentences,
		- other initialization
		  collapsed:: true
			- like other data types, `string str2 = str;` is vaild,
			- repeat character: `string str(3, 'c');` equals to `string str = "ccc";`
		- difference from C
		  collapsed:: true
			- the C syntax `char strC[10] = "CPP";`is still valid, but `strC` here is *not exactly* a "string",
			- many string syntax may not applies to `strC`; syntax on `strC` cannot apply to C++ string as well,
			- so it's better to use only one data type in code,
	- operations
	  collapsed:: true
		- input/output
		  collapsed:: true
			- as a bulit-in class, the basic I/O of string is easier than C,
			- input `std::cin >> str;`, output `std::cout << str << std::endl;`,
			- `getline(cin, str);`will use whole line(including space) and assign it to `str`, end by enter,
		- operator
		  collapsed:: true
			- `str2 = str1;` is valid, like C `strcpy`,
			- `str1 + str2;` is valid, like C `strcat`,
			  collapsed:: true
				- *at least one* operand to *each* + operator must be of string type,
				- like add two string literals `string s2 = "C" + "PP";` is illegal, while `str + "CPP";`, ` "C" + str + "PP";`are both valid,
			- `str1 == str2;` is valid, like C `strcmp`,
			  collapsed:: true
				- other compare operators are also valid, like `str1 != str2;`, `str1 < str2;`,
				- comparisons are case-sensitive and use dictionary ordering,
		- subscript operator `[]`(index)
		  collapsed:: true
			- `str[i];`return a char value, positions start at 0,
			  collapsed:: true
				- the `[]`operator receives a `string::size_type`value and return a reference variable of given position,
			- subscript outside the range or an empty string is undefined,
		- functions
		  collapsed:: true
			- `str.empty();`
			  collapsed:: true
				- return a bool about whether str is an empty string`""`,
			- `str.size();`
			  collapsed:: true
				- return a (unsigned) integer of the length of str, like C `strlen`,
				  collapsed:: true
					- actually returns a `string::size_type` value,
					- because length of some string might be quite big, so common integer may face overflow,
					- use `auto len = str.size();` could avoid the problem,
			- cctype library
			  collapsed:: true
				- ![image.png](../assets/image_1666948412397_0.png),
	- vector
	  collapsed:: true
		- concept
		  collapsed:: true
			- like an class(actually a class "template") version of C's `array`,
			- all elements must be the *same* type, and not limited to char,
		- initialization
		  collapsed:: true
			- `vector<int> ivec;`
			  collapsed:: true
				- vector is not a data type or class, actually, it is a "template" that *generate* class with given data type,
				  id:: 635ba1d6-fa38-427d-9c37-b4b6003ae2b9
				- so angle bracket `<>` is used here,
			- unlike Carray, declare the *length* of vector is *unnecessary*,
			- the data type could be any common type, as well as a vector, like `vector<vector<int>> ivec;`,
			- like Carray, vector need to be initialized like `vector<int> ivec = {1, 2};`,
			  collapsed:: true
				- list initialization`vector<int> ivec{1, 2, 3};` is also valid,
				- unlike C, assignment *after* declaration is also valid, like`vector<int> ivec; ivec = {1, 3};`,
			- direct initialization
			  collapsed:: true
				- `vector<int> ivec(3, 1);` is valid and equals to`vector<int> ivec{1, 1, 1};`,
				- `vector<int> ivec(3);` is also valid, but the parameter means ivec's *amount* of elements, all set to default value,
				- array initialization
				  collapsed:: true
					- arrays can be used to initialize vectors,
					- likes `int arr[10] = {1, 2, 3}; vector<int> ivec(arr + m, arr + n);`, will use value from `arr[m]` to `arr[n]` to fill the vector,
		- operations
		  collapsed:: true
			- the operation of vector is similar to string,
			- operator
			  collapsed:: true
				- operators are valid when vectors' elements have the same type(the length don't need to be same)
				- `ivec2 = ivec1;`is legal, but`ivec1 + ivec2;` is illegal,
				- `ivec1 == ivec2;` is valid,
				  collapsed:: true
					- other compare operators are also valid,
					- comparisons use dictionary ordering, and depends on the elements' datatype,
			- subscript operator `[]`(index)
			  collapsed:: true
				- `ivec[i];`return the element, positions start at 0,
				- index is allowed to be statements, like`ivec[num / 10];`
				- like string, subscript outside the range or an empty vector is undefined,
			- functions
			  collapsed:: true
				- `ivec.empty();`
				- `ivec.size();`
				  collapsed:: true
					- return a (unsigned) integer of the number of elements,
					  collapsed:: true
						- like string, the `[]`operator's type is corresponding `size_type`,
				- `ivec.push_back(i);`
				  collapsed:: true
					- like python's `append`, append given element`i` to the end of the vector,
	- iterator
	  collapsed:: true
		- concept
		  collapsed:: true
			- similar to pointer, while only used to fetch elements in *abstract data types*,
			- unlike pointer, iterator is *not* exactly the *address* of the element, and cannot be printed,
			- unlike string and vector, many "containers" don't support subscript method, while iterator is usually available,
		- initialization
		  collapsed:: true
			- `auto b = ivec.begin();`return an iterator points to the first element,
			  collapsed:: true
				- iterators are bound with abstract datatypes, so  address operator`&` not using there,
				- the precise type is `vector<int>::iterator`, while use `auto` will simplify the declaration,
			- `auto e = ivec.end();`return an iterator points to "off the end",
			  collapsed:: true
				- usually used as an *indicator* to check whether the iterator have iterate all elements, like `if (b != ivec.end())`,
				- sothat `e` does *not* points to element, and should not be used to fetch elements,
			- cbegin and cend
			  collapsed:: true
				- c means `const`, no matter whether the vector is const, cbegin and cend method will always return const iterators,
				- it is often used on when we don't want to change the value,
		- operations
			- dereference
				- like pointer, `*` operator is used to fetch the element,
			- arrow method
			  collapsed:: true
				- combine fetch operation and class'  method; `iter->method;`is equal to `(*iter).method;`,
				- add parentheses is better when using dereference variables, like `(*b)`; or use arrow operator `->`,
			- operator
			  collapsed:: true
				- arithmetic
				  collapsed:: true
					- `++iter;` increments `iter` to refer to the next element,
					- `--iter;` decrements `iter` to refer to the previous element,
					- operators *do not check* whether the iterator is still valid, so explicit comparison is always required,
				- other arithmetic
				  collapsed:: true
					- `vector` and `string` defined addtional operations(like arithmetic)
					- like `iter + n;`, `iter - n;`are both valid, n is an integer,
					- thus, for `vector` and `string`, iterator is quite similar to subscript,
					- `iter2 - iter1;` sometimes is valid and returns the *distance* between these two elements,
					  collapsed:: true
						- the distance could be negative or positive,
						- it returns an `difference_type`variable, so it's better to use `auto n = iter2 - iter1;`
				- comparison
				  collapsed:: true
					- `b1 == b2;`is valid, and iterators are equal if they denote the same element or if they are both off-the-end iterators,
					- for most containers, `<`and `>`is not defined, so `==`and `!=`is used more,
					  collapsed:: true
						- `vector` and `string` are commonly used, so they defined the comparison operator,
			- functions
	- array
	  collapsed:: true
		- only include new features in C++,
		- initialization
		  collapsed:: true
			- because arrays have fixed size, so they must initialize with literal indexes or "constexpr", like `int arr[10];`
			- arrays don't require initialization, and all elements are set to different default values according to their types,
		- functions
		  collapsed:: true
			- head file `<iterator>` defines `begin` and `end` functions for array,
			- like iterator, `int* abegin = begin(array);` is a pointer points to the first element(equals to `array` itself), and `int* aend = end(array);` is a pointer points to "off the end",
		- multidimensional array
		  collapsed:: true
			- initialization
			  collapsed:: true
				- reading from inside to out is helpful,
				- like `int mda[3][4];`
				  collapsed:: true
					- start from the identifier(name),
					- `mda[3]`means mda is an array of 3 elements,
					- `[4]` means each element has four children element,
					- `int` means elements of the children element is int,
				- in fact, `int mda[3][4] = {0,1,2,3,4,5,6,7,8,9,10,11};`has the same meaning of `int mda[3][4] = {{0,1,2,3}, {4,5,6,7}, {8,9,10,11}};`; while the former is easier to understand,
			- range for
			  collapsed:: true
				- ```
				  int mda[3][4] = {0,1,2,3,4,5,6,7,8,9,10,11};
				  for (auto &row : mda)
				  {
				      for (auto &col : row)
				      {col++;}
				  }
				  ```
				- the accurate type of row is `int (&row)[4]`, a reference to an array, while use auto is easier,
				- however, even we don't want to change the value, the reference can't be ignored either; otherwise the range for won't work,
				- sothat when we don't want to change the value, it's better to use a `const` qualifier,
			- pointers
			  collapsed:: true
				- for two-dimensional array, need to declare pointer as a *pointer to array*, which writes as `int (*p)[n];`,
				- for three(and more) dimensional array,  the correct type point to the first element(array) of`int mda[3][4][5];`is `int (*pmda)[4][5] = mda;`,
				- use `auto` is usually easier,
				- `int **` type *not equals* to `int (*)[4]`,
			- type alias
			  collapsed:: true
				- using `typedef` to give child array an alias may be helpful to use them,
				- while the syntax is `typedef int intArray[4];`, not `typedef int[4] intArray; `
				- however, the syntax of `using` is `using intArray = int[4]; `,
			- `begin` and `end` functions also works on multidimensional array,
	- `std::size`function
	-
	- ### user-defined types
	  collapsed:: true
		- Enumerations
		  collapsed:: true
			- a simple map between string and number(integer),
			- C's enum,
			- scoped enum : different from C, defined with`enum class Color {Red, Green, Blue};`, and need to use with `Color::Red`,
			- initialize with default value is valid, like `enum class Color {Red, Green = 3, Blue};`,
			- usually using with `switch`,
			- `Color CO = Color::Green;`will define CO as *Color::Green*,neither string `Green`nor int `3`,
		- Unions
		  collapsed:: true
			- similar to `struct`, which is also a group contains many data types, but only *one* of them can be used,
			- the initialization is similar to `struct` as well, like `union student{char name[10]; float height, weight;};`，
			- elements in the union could be approached through dot method, like `TOM.name;`,
			- union stores every value in tht same memory, and takes up as much memory as its largest member; that might cause problems because different data types has different expressions,
- Data type declarators
  collapsed:: true
	- @lvalues and rvalues
	  collapsed:: true
		- the concept is always bind with pointers and references,
		- when we use an object as an *rvalue*, we use the object's *value* (its contents); when we use an object as an *lvalue*, we use the object's "identity" (its *location* in memory),
		  id:: 638afecd-ee09-4ca0-8bcc-4e62421e093d
		- one important point is we can use an lvalue when an rvalue is required, but we cannot use an rvalue when an lvalue (i.e., a location) is required,
		- lvalues and rvalues are differ when used with `decltype`,
	- modifier
	  collapsed:: true
		- By default, type modifiers bind right to left,
		  collapsed:: true
			- like `int *p;`means p is an `int*`,
			- *parentheses* can *change* the priority, like `int (*parr)[10];` means a pointer to an array(usually used in multidimensional arrays)
			- for parentheses, like `int (*parr)[10];` reading from *inside to out* is helpful,
			  collapsed:: true
				- start from the identifier(name),
				- `(*parr)`means parr is an pointer,
				- `[10]`means it points to an array,
				- `int` means elements of the array is int,
		- pointers
		  collapsed:: true
			- definition
			  collapsed:: true
				- `int num = 1; int* p = &num;`,
				- `p` is the pointer,  type is `int*`, and the value is `&num` (address),
				- `*p` is the integer, and the value is `num`,
				- (address space layout randomization)
			- initialization
			  collapsed:: true
				- data type of the pointer and the variable which the pointer points to must *match*,
				- it is valid to define a pointer without initializing, however, these pointers have undefined value and is troublesome,
				  collapsed:: true
					- it's better to define a pointer only *after the object* to which it should point has been defined,
					- and always initialize other pointers to `nullptr`,
			- other pointer value
			  collapsed:: true
				- `void` pointer
				  collapsed:: true
					- a pointer has no data type, but might bound to one variable,
					- initialize
					  collapsed:: true
						- use keyword `void`,  like `void *pv = &var1;`,
					- property
					  collapsed:: true
						- void pointer can hold the address of any data type, and be assigned with any pointers,
						  collapsed:: true
							- `void *pv = &var1;`, var1 can be any variable,
							- `void *pv = p1;`,p1 can be any pointer,
						- the address held by the void pointer cannot be printed,
						- the variable located in the address cannot be changed through the void pointer,
					- usage
					  collapsed:: true
						- void pointer is usually used in managing the *memory itself*, instead of managing the *variable* located in the memory,
				- `std::byte` pointer
				  collapsed:: true
					- usually used with bit-wise and arithmetic operations,
				- `nullptr`
				  collapsed:: true
					- a pointer not bound to any variable, usually used to detect whether a pointer is `nullptr`, like `p1 == nullptr`,
					- initialize
					  collapsed:: true
						- use the literal `nullptr`, which could be converted to any other pointer type after,
						  collapsed:: true
							- (more in C)use `NULL` from `cstdlib`,
						- use literal constant 0,
						- `int *p1 = nullptr; int *p2= 0;`,
				- any values different from precedings are invalid,
			- operations
			  collapsed:: true
				- basic(`&` and`*`)
				  collapsed:: true
					- `&` and`*` are used as *both* an operator in statements and as part of a declaration,
					  collapsed:: true
						- it is important to distinguish the usage from the *context*,
						- operator always bound with it's right-hand *variable*,
						  collapsed:: true
							- `int* p1, p2;` equals `int *p1; int p2;`, not `int *p1; int *p2`,
							- `int` is the base declaration keyword,
						- assignment always changes its left-hand operand, sothat read the definition right to left might be helpful,
					- `&`operator : address-of "variables"
					- `*`operator : dereference "address"
				- lvalue and rvalue
				  collapsed:: true
					- dereference operator can use as both lvalue and rvalue,
					- after initialization`int num = 1; int* p = &num;`, both `int numb = *p;` and `*p = 13;`are valid,
				- pointer arithmetic
				  collapsed:: true
					- the most commonly used arithmetic operators are increment`++` and decrement `--`,
					- and most of other arithmetic operation on pointer is useless,
				- pointer comparison
				  collapsed:: true
					- null pointer means `false`,  and any other nonzero pointer means `true` ,
					- Two pointers are equal`==` if they hold the same *address*(always mean the *variable points to* , but has exceptions) and unequal otherwise,
					- null pointers are all equal,
					- a pointer used in a condition or in a comparsion must be valid,
			- pointers to pointers
		- (lvalue) references
		  collapsed:: true
			- concept
			  collapsed:: true
				- used as an *alternative of pointers*,
				- references are safer(reduce the risk of dereference a nullptr), but their function is less than pointers,
				- need to bind with an *existing* variable, cannot bind with literals(`int &r1 = 512;`is illegal),
				- cannot bind with *other* variables after initialization,
			- definition
			  collapsed:: true
				- `&`operator
				  collapsed:: true
					- `int num = 1; int& r = num;`
					- like pointers, the operator is bound with the variable name,
				- type of a reference and the variable which the reference refers to must *match*,
				- `&`bind with *variables* means *address-of*, like `&num`,
				- `&` bind with *data types* means *reference*, like`int& `,
			- property
			  collapsed:: true
				- reference don't need dereference operations, so they are similar to a *alias* of an variable,
				- the operation on reference variable will act on the original variable,
				  collapsed:: true
					- sothat defining an reference to an reference is vaild, while it might be meaningless,
			- operations
	- qualifier
	  collapsed:: true
		- const(constant)
		  collapsed:: true
			- concept
			  collapsed:: true
				- prevent other statement form changing the value of the variable(always for safety),
				- a const variable must be initialized because the value of it cannot be changed,
			- scope
			  collapsed:: true
				- by default, const variable has local(file) scope,
				- to share variable across multiple files, use `extern` keyword on *both* its definition and declaration,
				  collapsed:: true
					- `extern const int VAR = 512;  //definition`
					- `extern const int VAR;  //declaration `
			- const pointers
			  collapsed:: true
				- point to const(low-level const)
				  collapsed:: true
					- concept
					  collapsed:: true
						- syntax is `const int *p1 = &num1;`
					- property
					  collapsed:: true
						- variable's value cannot be changed *through pointer*,
						  collapsed:: true
							- while the value could be changed(for example, through assign`=` to identifier),
						- the pointer can point to other variable,
						- the rvalue cannot be other types,
				- const pointer(top-level const)
				  collapsed:: true
					- concept
					  collapsed:: true
						- means the pointer itself(address) is const,
						- the syntax is a little different `int *const p2 = &num2;`,
						- const pointers must be initialized,
					- property
					  collapsed:: true
						- unlike reference, pointers are variable, so there are "const" pointer,
						  collapsed:: true
							- and "const pointer" are not exactly as same as "const reference",
						- const pointer can be used to change the value,
				- usage
				  collapsed:: true
					- *const variable* must used with "point to const" pointers,
						- for `const int var1 = 12;`,
						- `const int *p1 = &var1 //p1 must point to const`,
					- "const variable", "const pointer", "point to const" are not same, while the difference is tedious and not worth paying too much attention,
					  collapsed:: true
						- for example, *pointer to const* might not point to a const variable,
						- `int var1 = 12;`, `const int *p1 = &var1 //var1 not must be const`,
			- const references
			  collapsed:: true
				- concept
				  collapsed:: true
					- "const reference" usually means a *reference to const*,
				- property
				  collapsed:: true
					- like pointers, variable's value cannot be changed *through reference*,
					  collapsed:: true
						- while the value could be changed(for example, through assign`=` to identifier),
					- the rvalue can be any "convertible" type,
					  collapsed:: true
						- `const int &r1 = 512;`is valid, and the result is similar to `const int r1 = 512;`,
						  collapsed:: true
							- `const int temp = 512; int &r1 = temp;`,
							- temporary variable is an unnamed variable created by the compiler,
						- `const int &r1 = 1.12;` is vaild, while `int &r1 = 1.12;` is illegal,
						  collapsed:: true
							- because "const reference" actually initialize a temp variable, and assign the value to the temp variable; that's the convert applies,
				- usage
				  collapsed:: true
					- *const variable* must used with const references,
			- const method
			  collapsed:: true
				- only used with Class' methods(not worked on normal functions)
				- report a mistake when method change members,
				- to avoid potential modification, const references and pointers *cannot* invoke methods that are *not const*,
				  id:: 63c120e9-5f5b-46cc-ba4f-30cf08213de4
		- constant expression
		  collapsed:: true
			- concept
			  collapsed:: true
				- constant expression means the value is determined at *compile time*, and the value is const sothat it will *not changed* through the program, like`const int num = 12;`,
			- purpose
			  collapsed:: true
				- `int numa = 12; const int num = numa;` is not,
				  collapsed:: true
					- although num *is const*, numa isn't,
					- so the compiler cannot determine the value of num,
				- `const int num = func();`is not,
				  collapsed:: true
					- because the value need to be calculated from the context statements,
					  id:: 63510990-3175-47fa-bb30-cff6d8726f6f
			- initialization
				- variable which has constant expression should be"literal types",
				  collapsed:: true
					- which means these types has corresponding "literal value",
					- including int, reference, pointers
					- by comparsion, class variables(like string) are usually not,
			- `constexpr`
				- for a clearer understanding, new variables initialized as `constexpr` *restrict* the initialization to be const expressions,
				  collapsed:: true
					- `constexpr int num = 12;` is similar to `const int num =12;`
					- while`const int num = func();`,`const int num = othernum;` is vaild only if `func()` is a const expression, and `othernum` is a const,
				- pointers
				  collapsed:: true
					- `constexpr int *p = &num;` is *same as* `int constexpr *p = &num;`which both make the *pointer* const,
					  collapsed:: true
						- that is `int const *p`, not `const int *p`
					- for `constexpr int *p = &num;`,
					  collapsed:: true
						- `num` need to have "static storage duration",which means `num` cannot initialize in functions,
						- but num don't need to be `const`,
					- `constexpr int *p = nullptr;` is valid,
				- usage
				  collapsed:: true
					- to make sure a variable is const, it's a great idea to use keyword `constexpr`,
	- specifier
	  collapsed:: true
		- introduction
		  collapsed:: true
			- because C++ has static data types, the data type of the return value of an expression should be determined at first,
			- however, in complex functions, this could be quite difficult to do,
		- auto
		  collapsed:: true
			- concept
			  collapsed:: true
				- `auto` tells the compiler to deduce the data type from the initializer,
				- variable defined as `auto` must be initialized at definition,
			- syntax
			  collapsed:: true
				- basic
				  collapsed:: true
					- `auto` is similar to other primitive data types in usage,
					- `auto` can used on most *bulit-in* types,
					  collapsed:: true
						- `auto num1 = 12;`,
						- `auto string1 = "CPP";`
					- multi-initialization is vaild, while the type need to be consistent,
					  collapsed:: true
						- `auto num1 = 1, num2 = 2;`is vaild,
						- `auto num1 = 1, num2 = 2.1;`is illegal,
				- syntax on const
				  collapsed:: true
					- auto ordinarily *ignores* (previous) top-level consts, sothat top-level const need to declare explicitly,
						- like`const int num1 = 12; auto num2 = num1;`, num2 is not const,
						- need to use `const auto num2 = num;`,
					- while low-level consts are kept,
						- like`const int num1 = 12; auto point2 = &num1;`, point2 still point to const,
		- decltype
		  collapsed:: true
			- concept
			  collapsed:: true
				- variable defined as `auto` must be initialized at definition,
				- by comparsion, variable defined as `decltype` doesn't required initialization at definition,
				- while for specific types(like const variable or references), the variable still need initialization,
			- syntax
			  collapsed:: true
				- the syntax is similar to `auto`, `decltype (statements) var;` will deduce the type of `statement` and use it to define `var`,
				- like `int num1 = 12; decltype (num1) num2;`will define num2 as int,
				- others
				  collapsed:: true
					- decltype will remain top-level const,
					- decltype with double parentheses`decltype((variable)) var1` is always a reference type,
	- alias
	  collapsed:: true
		- typedef
		  collapsed:: true
			- concept
			  collapsed:: true
				- give a *data type* an alias for further using,
				- `typedef double DB; DB num = 1.1;`
			- property
			  collapsed:: true
				- typedef allows multi-define separated by comma
					- like `typedef double DB, *PD;` means `typedef double DB;`and `typedef double* PD;`,
				- usually the original name is still available,
			- modifiers
			  collapsed:: true
				- `typedef double* PD; PD p = &num;` is vaild,
					- it is useful on some scenario, like defining nested arrays`**p`,
					- but make code more hard to read,
		- using
		  collapsed:: true
			- concept
			  collapsed:: true
				- `using DB = double;` is similar to `typedef double DB;`, which gives `double` an alias,
		- qualifier on alias
		  collapsed:: true
			- const
				- for `const PD pd1 = &num;`, const works on the *base type* `double*`
				  collapsed:: true
					- which means after`typedef double* PD;`,
					- `const PD pd1 = &num;`looks like `const double* pd1 = &num;`,
					- but the first define a *const pointer,* and the second define a *pointer to const*,
					  id:: 63511321-180f-4125-9b14-9bfedc626285
					-
- Object life cycle
  collapsed:: true
	- constructor and destructor
	  collapsed:: true
		- constructor is called after variable's storage duration begins, and the destructor is called before that variable's storage duration ends,
	- scope
	  collapsed:: true
		- concept
		  collapsed:: true
			- namespace avoids inadvertent collision between functions,
			- most scopes in C++ are delimited by curly braces`{}`,
		- operator
		  collapsed:: true
			- operator `::`,
			  collapsed:: true
				- prefix `std::`indicates function `cout` and `cin` are defined inside the namespace `std`,
			- `using` declaration
			  collapsed:: true
				- with `using std::cin;` the `cin` function could be used without namespace,
				- this declaration is required for each function,
				-
		- global(outer scope)
		- block(inner scope)
		  collapsed:: true
			- redifined
			  collapsed:: true
				- variable can be *redifined* in inner scope, and the new value will be used,
				- need *explicit declaration*(scope operator) to reuse the original value defined outside,
			- concept
			  collapsed:: true
				- ```
				  for (int i = 1; i < 10; i++)
				      {
				         int j = 10;
				         /*variable "initialized" in block 
				           will be discarded after block, */    
				      }
				  
				  auto var = i / j;
				  //i and j are undefined,
				  ```
			- keyword `static`
			  collapsed:: true
				- variables declared as `static` won't be destroyed after block execution,
		- namespace
		  collapsed:: true
			- defined inside a namespace
	- duration types
	  collapsed:: true
		- automatic duration
		  collapsed:: true
			- usually called "local" variables,
		- static duration
		  collapsed:: true
			- declared with keyword `static` or `extern`,
			- local static : local variables have automatic duration unless they are defined with `static`,
			- static Class member : like local variables, Class *members* defined with `static` can be used (through scope operator`::`) without *instances*,
		- dynamic duration
		  collapsed:: true
			- keyword `new` and  `delete`
			  collapsed:: true
				- the replacement of C's `malloc` and `free`,
			- `new` works with given type and returns a *pointer*, like `int* nump = new int;`,
			  collapsed:: true
				- initialization is valid, like `int * nump = new int{42};`,
			- `delete` works with the *pointer*, like `delete nump;`,
			  collapsed:: true
				- however, compiler *doesn't* typically clean up memory after an object is deleted,
				- so the deleted variable should not be used anymore,
			- objects have dynamic duration *won't* be deleted (even program ends) unless *manually use* `delete` keyword,
		- @thread-local duration
- Operations and Functions
  collapsed:: true
	- basic operators
	  collapsed:: true
		- arithmetic operators
		  collapsed:: true
			- division
			  collapsed:: true
				- basic
				  collapsed:: true
					- truncate the decimal, like `30 / 6 == 5`, `31 / 6 == 5`, the result is integer,
				- float
				  collapsed:: true
					- when one variable is float, other variables will be "promotion" to float, thus the result is float,
				- reminder
				  collapsed:: true
					- *cannot* use with float,
					- m%(-n) is equal to m%n,  and (-m)%n is equal to -(m%n);
					- that is `21 % -8 == 5;`, `-21 % 8 == -5`, and `-21 % -8 == - (21 % -8) == -5;`,
			- compound arithmetic operators(increment and decrement)`++, --`,
			  collapsed:: true
				- prefix `++i`first increment i, then use the new value(i + 1),
				- postfix `i++` first use i's value, then increment i,
			- compound assignment operators`+=, -=`,
		- logical operators
		  collapsed:: true
			- ![image.png](../assets/image_1667552406621_0.png),
			  id:: 6364d3d5-f7fb-4e53-aa28-00ffed719a68
			- bool value shouldn't be used in comparison, `(var == true)` actually means `(var == 1)` due to the type conversion; use `(var)`  is simpler and more efficient,
			  id:: 6364d5b9-27a0-447a-9b13-2b3586101786
		- @bit(bitwise) operators
		  collapsed:: true
			- ![image.png](../assets/image_1667556282121_0.png),
			- integer
			  collapsed:: true
				- In fact, there are *not* bit *data types* in C++, so these operators usually work on integers,
				  collapsed:: true
					- bit operators work on *every* bit, so the result usually depends on how many bits compiler used to present the integer,
					  collapsed:: true
						- ![image.png](../assets/image_1667638343162_0.png)
					- it's better to use `unsigned` types with bit operators,
						- left shift on the sign bit is undefined,
				- following examples assume int is presented by 32 bits,
				  collapsed:: true
					- ![image.png](../assets/image_1667638894577_0.png),
					- ![image.png](../assets/image_1667639102673_0.png),
					- ![image.png](../assets/image_1667639222649_0.png),
					  id:: 636621da-7005-4184-8897-03e10b0632f5
			-
		- @comma operator
		  collapsed:: true
			- used with for loop,
		- operator overloaded
		  collapsed:: true
			- overloaded operator has the *same precedence* and associativity as the built-in version of that operator,
			-
		- operator priority(precedence)
		  collapsed:: true
			- assignment has lower precedence, so it's better to use parentheses, like `((i = func()) != 1)`,
			- increment and decrement operators usually have the highest precedence,
			- complete precedence table
			  collapsed:: true
				- ![image.png](../assets/image_1667815532172_0.png),
				- ![image.png](../assets/image_1667815560751_0.png),
				- ![image.png](../assets/image_1667815576896_0.png),
				- ![image.png](../assets/image_1667815592104_0.png),
				-
		- order of evaluation
		  id:: 6364ce75-d755-446f-9a4f-25f094b9b0c8
		  collapsed:: true
			- most operator doesn't guarantee *which operand* will be calculate *first*,
			- so it's better not to use the statements that change the same object on different operands, like (`int t = func1(i) * func2(i);`),
			- four operators are exception, logical AND`&&`, logical OR `||`, condition `?:` and comma`,`,
			- they both calculate the left statement first,
	- assignment
	  collapsed:: true
		- definition
		  collapsed:: true
			- creates memory space for values,
			- default value
			  collapsed:: true
				- uninitialized variables of built-in type defined outside functions are initialize to 0,
				- while for those inside a function(include `main` function) are uninitiated("undefined" value),
				- class variables(instance) have a value that is defined by the class,
				  collapsed:: true
					- most class defined a default value,  such as string's default value is `""`,
					- some class prohibit defining an instance without initialization, result in the mistake reported by the compiler,
			- suggestions
			  collapsed:: true
				- it's better to define an variable near the point at which the object is *first used*, which make it easy to find the definition,
				- it is recommended to *initialize* each variable *as long as* it is declared, this will make program safer because undefined variable is hard to find,
		- initialization
		  collapsed:: true
			- assign specified *value* to the variable at the moment it is *created*,
			  collapsed:: true
				- "initialization" is somewhat complicated in C++,
				- initialization and assignment are *different* operations in C++; assignment means *replaces* the value of an *existing* variable,
				  id:: 6347d516-7044-4aa8-b2d2-cbb6e1e67bad
				- although the distinction often doesn't matter,  it may cause errors in coding,
			- braced initialization`{}`
			  collapsed:: true
				- use curly braces for initialization
				  collapsed:: true
					- `int num{0};` is legal initialization statements, equivalent to `int num = 0;`,
					  collapsed:: true
						- use the equals-plus-braces is also valid, like `int num = {0};`
					- *empty* braces is valid ,and it will initialize variable will *default* value,
					- only for *initialization*, not for *assignment*; like `int num; num{0};`is illegal,
				- property
				  collapsed:: true
					- loss of information assignment will *report error*,  like assign a `long` to `int`; by comparison,
					  collapsed:: true
						- by comparison, common assignment operation is legal with cutting(truncate) the value,
					- always used in initializing multi-value data type, like`vector <int> ivec = {1, 2, 3};`;
					  collapsed:: true
						- for that usage, every value need to be the *same* , like`vector <string> istr = {3, "CPP"};` is ambiguous,
					- @always applicable no matter the object's *scope* or type,
				- it's recommended to always use braced initialization,
			- direct initialization`()`
			  collapsed:: true
				- use parenthesis for initialization
				  collapsed:: true
					- `int num(0);` is legal initialization statements, equivalent to `int num = 0;`
					- only for *initialization*, not for *assignment*; like `int num; num(0);`is illegal,
				- property
				  collapsed:: true
					- always used to initialize with multi-*parameters*(not value),
					- usually first is the amount, and second is the value, like `string str(3, 'c');` equals to `string str = "ccc";`,
					- the initial value sometimes could be variable, like `int numa = 1; int numb(numa);`,
		- declaration
		  collapsed:: true
			- makes a name(identifier) *known* to the program, so that the compiler will try to find the definition elsewhere,
			  collapsed:: true
				- "declaration" and "definition" are different operations,
				- keyword "definition" is more like the traditional "declaration",
				- while "declaration" means pointing out the name(identifier), most times *without allocating memory* space,
			- keyword `extern`
			  collapsed:: true
				- `extern int i;` is a "declaration", which tells the compiler to find the "definition" elsewhere,
				- however, extern with an initializer will *override* the extern keyword, like `extern double pi = 3.1416;`,
				  collapsed:: true
					- this statement is legal, but will cause error most times,
					- this statement inside functions is not allowed,
		- identifiers(names)
		  collapsed:: true
			- must begin with either a letter or an underscore,
			- identifier began with an underscore is usually used inside functions,
	- @copy
	  collapsed:: true
		- transfer by value(default)
		- @copy constructor
		  collapsed:: true
			- for class instance, shallow copy might lead to mistakes,
			  collapsed:: true
				- for example, if instances have pointers, then the copy will have another pointer point to the *same memory,*
				- the memory will be freed after one instance is deleted,  thus another instance's delete will cause mistake,
			- for classes, define a copy *constructor* `classA (const classA& other);`and copy with brace like`classA Ib{Ia};`will make a deep copy,
		- @copy assignment
	- @move
	  collapsed:: true
		- concept
		  collapsed:: true
			- "moving" an object y into an object x is not "renaming", because they have separate storage and might have different lifetimes,
		- rvalue reference
		  collapsed:: true
			- defined with `int&& var;`,
	- control flow
	  collapsed:: true
		- null statement
		  collapsed:: true
			- statement only has a `;`, like python's `pass`; often using in loops,
			- like `while (cin >> str && str != sought) {; // null statement}`,
			- should be commented,
		- condition
		  collapsed:: true
			- if-else
			  collapsed:: true
				- `if (condition) {statements;} else {statements;}`，
				- (if necessary),`else if(condition) {statements;}`,
				- `else` statement is not compulsory, and program won't do anything if the `condition` is false,
			- switch
			  collapsed:: true
				- `switch(statement) case(integer1): {statements;}case(integer2): {statements;} default: {statements;}`
				  collapsed:: true
					- `default`is not compulsory,
					- `case`should be (one) const integer(or char) expression, and usually is literal,
					  collapsed:: true
						- the integer here is not exactly a "condition"(a `bool` value), so type conversion won't happen,
				- the number of cases is unlimited,
				- `break;`is *usually* needed, because as long as one result matches, switch will continue to execute *every following* statements *without* checking the further result,
				- `switch`could be replaced by multiple `else if`, like `if(statement = integer1){statements;} else if(statement = integer2){statements;} else {statements;} `
			- conditional operator
			  collapsed:: true
				- like a simpler if-else statement,
				- the result is rvalue at most times, so it usually use in assignments,
				- `= (condition) ? statements1 : statements2 ;`, like `int k = (i == j) ? i++ : i--;`,
				- conditional operator has lower precedence, so it's better to use parentheses,
		- loops
		  collapsed:: true
			- while
			  collapsed:: true
				- `while(condition) {statements;}`,
				- `do while` will make sure the statement will execute at least one time, like `do {statements;} while (condition);`
			- for
			  collapsed:: true
				- `for(initialization; condition; increment){statements;}`
				- initialization could has multiple statements,
				- each statement in for's `()` can be omitted, while a null statement`;` is still *required* instead of only space, like `for(; condition;){statements;}` is valid and similar to a while loop,
			- range for
			  collapsed:: true
				- concept
				  collapsed:: true
					- similar to common for loop, range for iterates through *elements* in a given *sequence*(like arrays, vectors or strings), and performs some operation on each element,
					- like`for (char c : str1){statement;}` will iterate each char of given string `str1`,
				- syntax
				  collapsed:: true
					- `for (auto i : sequence){statements;}`,
					  id:: 638afecd-2fd5-4dc8-8705-aa5f08c831f4
					- ```
					  //range for is made by traditional for loops
					  for (auto beg = v.begin(), end = v.end(); beg != end; ++beg) 
					  {
					      auto &i = *beg; //sothat i must be a reference to change the value,
					  	statements;	
					  }
					  ```
				- property
				  collapsed:: true
					- change value
					  collapsed:: true
						- the loop variable need to defined as *reference type* to change the value, like `for (char &c : str) {c = toupper(c);}`,
						- `for (char c : str) {c = toupper(c);}`will not work,
					- because the beginning and ending is determined at initialization, so range for cannot be used to change the *length*,
		- others
		  collapsed:: true
			- `break;` will terminate the nearest loop and jump out,
			- `continue;` will terminate the nearest loop and jump back to condition checking,
			- (`goto;`)
		- nested control flow
		  collapsed:: true
			- control statements usually need to use nestly to achieve complex goals,
			- block corresponding
			  collapsed:: true
				- unlike python, C++'s statements match with curly braces`{}` instead of matching with *indentation*; so always type the curly brace is better,
			- progress checking
			  collapsed:: true
				- some times, print the intermediate result will be helpful,
	- functions
	  collapsed:: true
		- main function
		  collapsed:: true
			- arguments
			  collapsed:: true
				- main function can (only) accept two arguments, like `int main(int argc, char *argv[])`,
				- the integer`argc` indicates the amount of strings(actually C-strings `char str[]`) that main will receive(from command line), and those strings are stored in array `argv`, separated by space,
				- for example, `./hello aa bb 23` will pass value to variables `argc[0] == ./hello`, `argc[1] == aa`, `argc[2] == bb` and `argc[3] == 23`,
			- return
			  collapsed:: true
				- by convention, return value of 0 indicates success.
				- the meaning of nonzero return is defined by the system, different value usually means different kind of error,
				- command `echo $?` will show the status (number),
				- `main` can have no `return` statement, while other functions must have `return` as long as their return type is not `void`,
		- common functions
		  collapsed:: true
			- sizeof
			  collapsed:: true
				- return the size of the variable or the function as a constant expression(a *const* `size_t` value),
				  collapsed:: true
					- sizeof don't "operate" the variable, so dereference a null pointer is valid; like `int *p; sizeof(*p);`
				- `sizeof(var);`return the size(byte) of variables,
				  collapsed:: true
					- for example, `sizeof(char);`will always return 1;
				- `sizeof func;`return the size of `func`'s return variable,
				- usage
					- calculate the length of array, like`constexpr size_t L = sizeof(arr)/sizeof(*arr);`,
			- clock
			  collapsed:: true
				- defined in `<ctime>`,
				- basic syntax
				  collapsed:: true
					- `clock_t start, stop; start = clock(); statements; end = clock();`
					- `double duration; duration = ((double)(stop - start)) / CLOCKS_PER_SEC;`,
		- self-defined function
		  collapsed:: true
			- definition
			  collapsed:: true
				- like C, `int func(int arg) {statements;}`,
				- functions has no parameters is legal; `void` is usually used for that situation like `int func(void) {statements;}`, but not a must,
			- declaration(prototype)
			  collapsed:: true
				- concept
				  collapsed:: true
					- re-declare a function is legal, and is similar to re-declare a variable,
					- which means makes the name known to the program, and instruct the compiler to find the definition elsewhere,
					- like C, `int func(int arguments);`,
				- parameter
				  collapsed:: true
					- parameter's type is required, while the name `arguments` are not, like `int func(int);`,
					- adding name will make code more readable,
					- when functions have default arguments, these default value should only declare for *one time* on the *first appearance*  of the function,
					- ```
					  void printDB (double k, double i = 1.1, double j = 1.2);
					  printDB(1);
					  void printDB (double k, double i, double j)
					  {
					      std::cout << k << i << j << std::endl;
					  }
					  //(only) syntax above is legal, which sets default value in prototype,
					  
					  //however, add "other" default value below is legal, like
					  void printDB (double k = 2, double i, double j)
					  {
					      std::cout << k << i << j << std::endl;
					  }
					  ```
			- function overloading
			  collapsed:: true
				- concept
				  collapsed:: true
					- compiler can find the correct function by checking *both* the name and the *parameter* (type and amount),
					- which means functions that do *similar things* but worked on *different data types* can have same name,
					- one exception occurs when facing `int func(long a){};` and `int func(float a);`, although they are not the same, when passing `int` variables, *type conversion* might happen, so the function calling is still ambiguous,
				- const parameter
				  collapsed:: true
					- parameter's top-level const will be ignored, so `void func(const int var);`is the same as `void func(int var);`,
					- by comparison, low-level const won't be ignored, so `void func(int* var);` and `void func(const int* var);` will be treated as two different functions,
				- overload and scope
				  collapsed:: true
					- by default, it's not recommended to declare functions inside the function(block scope),
					- when calling functions inside block, the compiler will find the definition in the scope first, and as long as it finds the definition, it *won't* try to find definitions outside the scope,
					- so that if the definition doesn't match exactly, the compiler will report a mistake, like `void print(double db);  void func(  void print(string str); print(3.14);  )`(the parameter not match),
				- function matching
			- parameter and argument
			  collapsed:: true
				- argument passing
				  collapsed:: true
					- by convention, functions in C++ *will not* change the (global) variable's value,
					- the traditional argument passing activity actually use the *value* of argument to initialize *new* variables, then using them in the function, like`int par; par = arg;`,
					- that's why parameters need to explicitly initialize in the function's *definition*,
					- then all statements in the function work on the new variable, instead of the raw variable,
				- changing value (pointer and reference)
				  collapsed:: true
					- traditional **C**'s method to modify the raw variable is passing the pointer points to the variable,
					- the parameter and function's statements all need to change the variable to pointer type `int func (int *par)`,
					- initialize a pointer to argument and pass the pointer`int *p = &arg; func(p);`, or directly pass the address to function `func(&arg);` are both valid,
					- in **C++**, passing the reference is a new method to change the raw argument,
					- the parameter need to change the variable to reference type `int func (int &par)`, and other statements don't need to change,
					- and passing the original argument is enough`func(arg);`,
				- const parameter
				  collapsed:: true
					- the argument passing mechanism will make program slower when the argument is big,
					- passing the argument through reference(or pointer) will tranfer the original argument to the function, sothat it won't involve new initialization; but the value might be changed occasionally in function,
					- to avoid careless modification, use keyword `const` in parameter will be helpful, that will avoid modification statements in the function block; like `int func (const int& par);`
					- for `const` parameter, the argument passing to it don't need to be a `cosnt`; but `const` argument requires a `const` parameter,
					- it's recommended to *always use*  `const` on the reference parameter, unless the value really requires changing,
				- array parameter
				  collapsed:: true
					- array variable are actually passing to the function by pointer; so `int func (int a[]);` is similar to `int func (int* a);`, the argument they received are both pointer,
					- as a result, functions usually cannot determine the size of the array, and requires additional parameters,
					- one way is using the C++'s `begin` and `end` function, and passing both two arguments, like `int func(int* beg, int*end);`; while the argument should change to `begin(a)` and `end(a)`, respectively,
					- another way is calculating the length before and passing the length variable to function as well, like `int func(int *a, size_t len);`; although `int func(int a[10]);`might seem concise, that always don't works,
					-
				- multidimensional array parameter
				  collapsed:: true
					- the syntax is similar to common array, like `int func (int (*matrix)[10]);`; here the parentheses and the inner array's length is required,
					- using index like `int func (int [][10]);`is more concise, while the inner array's length is still required and must be compatible,
					- and calling array through index in the function body is legal,
				- varying parameters
				  collapsed:: true
					- `initializer_list`
					  collapsed:: true
						- template `initializer_list<type>` can receive varying arguments, and capsule these variables in a `initializer_list` variable(similar to a `vector`) through "list initialization",
						  id:: 636e0024-9ad3-4a2e-8a22-f38a12df48ce
						  collapsed:: true
							- all arguments must have *same type* and compatible with the default type,
							- and these arguments need to enclose in curly braces like `{1, 2, 4}`,
						- the operation on `initializer_list` variable is similar to `vector` too, and one difference is all the elements are `const`,
						- functions have `initializer_list`  parameter can receive other types of parameters,
					- ellipsis parameters(C syntax)
				- default arguments
				  collapsed:: true
					- parameter's order
					  collapsed:: true
						- ```
						  void printDB (double k, double i = 1.1, double j = 1.2)
						  {
						      std::cout << k << i << j << std::endl;
						  }
						  
						  /* void printDB (double i = 1.1, double k)
						  *  is illegal, parameters having default value must behind
						  *  those don't have default value,
						  
						  /* calling like printDB(1, 2, 4);
						  *  is legal, the input argument will cover the default value,
						  *  calling like printDB(, , 3);
						  *  is illegal, the compiler won't interpret the comma as seperation, 
						  */
						  ```
					- other default value
					  collapsed:: true
						- besides literal values, other variable can be used as default value as well,
						- such as functions(expressions) and  (global)variables,
			- return
			  collapsed:: true
				- value returning
				  collapsed:: true
					- similar to argument passing,  `return` initialize a new(temporary) variable with the value calculated from the function,
				- return with modifiers
				  collapsed:: true
					- reference calling
					  collapsed:: true
						- when operating *global* variables, using reference as return type could return the original variable instead of copying them, and `const` ia usually needed when using references,
						- like `const string& short(const string& s1, const string& s2) {return s1.size() <= s2.size() ? s1 : s2;}` returns the shorter string by calling it through reference,
						- while for variables initialized *inside* the function(that has block scope), because their memory will be freed after function's execution, return reference to these variables is illegal,
					- lvalue reference
					  collapsed:: true
						- calls to functions that return references are "lvalues",
						- so if the return is not `const`, the function could be used to *change* the *return variable*,
						- like `char& change(string& str, auto n) {return str[n];}` will return a reference to the char of `str[n]`; and that char could be changed through *assignment* `change(str1, 1) = 'A'`;
				- varying returns
					- similar to parameter, `vector`could receive varying return variables through "list initialization" and return a `vector`, like `vector<string> func(){return{"app", "bpp", "cpp"};}`
					  collapsed:: true
						- all variables must have *same type* and compatible with the default type,
						- and these variables need to enclose in curly braces like `{1, 2, 4}`,
				- use reference to "return" more value
				  collapsed:: true
					- functions can only return one variable,
					- one way to "return" more value is initialization one (global) argument first,
					- then pass the argument to the function by reference, sothat some results can be reserved in that argument,
				- return pointers to array
				  collapsed:: true
					- return normal pointer`int* func(int N){return arr;}`,
					- using type alias`typedef int arrT[10]; arrT* func(int i){}`,
					- basic syntax`int (*func(int i))[10]{}`,
					- using auto and "trailing return type"`auto func(int i) -> int(*)[10]{}`,
		- small functions
		  collapsed:: true
			- usage
			  collapsed:: true
				- "functions" are easily reuse and modify, and the syntax is always easier to understand,
				- but functions might consume more execution resources, including saving and restoring registers, and coping arguments,
			- lambda
			  collapsed:: true
				- `[capture] (arguments) {statements;}`,
				-
			- inline
			  collapsed:: true
				- one way to optimize *small* functions is using `inline` keyword, like `inline void func(int i){}`
				- `inline` will *request*(not force) the compiler to change all function calling to equivalent function statements, which won't make space for parameter and so on,
			- constexpr
			  collapsed:: true
				- functions be defined as `constexpr`are similar to other functions, but are restricted to use "literal type" parameters and return values,
				- actually, the parameter and return could be variables, as long as the variable is `constexpr`,
				- like`constexpr int scale(int cnt) {return 42 * cnt;} scale(i);`is valid as long as `i`  is defined as `constexpr`,
		- pointers to functions
		  collapsed:: true
			- concept
			  collapsed:: true
				- like other pointers, pointers to functions should match the function's *"type"*, which includes their *parameters'* type and *return* type,
			- quick example
				- function `int func(int num){};`has a `int` parameter and `int` return type,
				- thus the pointer should be defined like `int(*pf) (int);`,
				- then the function could assign to the pointer`pf = func;`,
				  collapsed:: true
					- the address operator`pf = &func;` is not required, while adding the operator is valid,
				- and pointer can be used like a function,`pf(3);` is equivalent to `func(3);`,
				  collapsed:: true
					- the dereference operator`(*pf)(3) ;` is not required, while adding the operator is valid,
			- type alias
			  collapsed:: true
				- if we know the function's name, using `decltype` and `typedef` could make that simpler, like `typedef decltype(func) pf;`, or `using PF = decltype(func);`;
				- here `decltype` returns *function* 's type, so explicitly `*` operator is required, like `typedef decltype(func) *pf;`,
			- using as parameter
			  collapsed:: true
				- pointers to functions could be used in parameters, and the type need to match,
				- like `int funcb(int a, int(*pf) (int)){};`,
				- it's better to use with type alias through `typedef` or `using`,
			- using as return value
			  collapsed:: true
				- pointers to functions could be used as a return type,
				- like ` int(*pf (int)) funcb(int a){};`,
				- it's better to use with type alias through `typedef` or `using`, or using trailing return,
- Input and Output
  collapsed:: true
	- <iostream> library
	  collapsed:: true
		- overall
		  collapsed:: true
			- consist of two components: istream and ostream,
			- "stream" is intended to suggest that the characters are generated, or used, "sequentially"(char by char) over time,
			  id:: 6343df54-f33c-4586-aff0-22c86d2c1740
		- output
		  collapsed:: true
			- printf(C syntax)
			  collapsed:: true
				- 基本语法
				  collapsed:: true
					- `printf("string", var1, var2...)`，
					- printf函数接受的主要参数只能为*单个字符串*（即"string"），或字符串变量（如str = "string"），
					- 需要使用占位符来输出其他变量（整型数，嵌套字符等），
				- 变量标记符（Specifiers）
				  collapsed:: true
					- 百分号`%`代表占位符，在输出时，字符串"string"中的占位符的位置会由指定的变量替代，
					  collapsed:: true
						- 可以使用%%来输出百分号，
					- 数值
					  collapsed:: true
						- 基本：`%d`接受int值，`%f`接受float值，short，long，long long，unsigned分别也有对应的指代，
						- 数字进制：对于同一整型数，%d可以显示十进制数字，%o和%x则会分别显示对应的八进制和十六进制数字，
						- 科学计数法：使用%e可以将对应数值按科学计数法输出，
					- 字符
					  collapsed:: true
						- 对应占位符为`%c`，
					- 字符串
					  collapsed:: true
						- 如果需要输出多个字符串，或将字符串变量嵌入语句中，则需要使用占位符`%s`，
				- 修饰符（modifiers）
				  collapsed:: true
					- 在%和变量标记符可以插入修饰符（数字或字母），
					- 示例：`%05.2f`表示打印一个浮点数
						- 5表示最小字段宽度为5字符，0表示数值有空缺时（此处为不到5位），用0补齐位数（不输入0则会用空白补齐），
						- .2表示小数点保留2位（精度），
						- f为浮点数的标记符，
				- 标记符（flags）
				  collapsed:: true
					- 在%和变量标记符可以插入标记符（符号或空格），
					- 示例：加入#号`%#x`则可以在进制数前显示表示进制的前缀，
				- 备注
				  collapsed:: true
					- 对于printf函数而言，不同的占位符表示指代的为数据的不同*显示*方式，并非数据的*存储*方式，因此同一字符可以输出为不同“格式”，
					- 例如，字符C会按照ASCII码存储为二进制`01000011`，使用%c会将其显示为C，使用%d会将其显示为67，而使用%o则会将其显示为103，
					- （printf函数不会加入换行符，因此一般在字符串末尾加入换行符以方便下一行输入），
			- cout
				- syntax `std::cout<< var1 << var2 << std::endl;`,
				  collapsed:: true
					- with `using namespace std;`, `std::`could be removed,
					- actually made of three output statement, `cout<< var1;`, `cout<< var2;`, `cout<< endl;`,
					- `var` could be any build-in(primitive) types, and literal values, while only one type could use between`<<`,
				- `endl` keyword
				  collapsed:: true
					- used to start a newline *and* flushing the i/o buffer,
					  collapsed:: true
						- if the program crashes, output may be left in the buffer, leading to incorrect inferences about where the program crashed,
						- this ensures that all the output the program has generated so far is actually written to the output stream, rather than sitting in memory waiting to be written,
					- if just want a newline, use `<<'\n';` is valid,
			- multiple outputs
			- `ostream`
		- input
		  collapsed:: true
			- scanf(C syntax)
			  collapsed:: true
				- 变量声明
				  collapsed:: true
					- 在使用scanf函数接受输入之前，应先声明需要用到的变量，
					- scanf是直接将输入赋值给指定的var1，因此不能与声明语句放在一起（如`var1 = scanf("%s", var1);`是不合法的），
				- 基本语法
				  collapsed:: true
					- `scanf("string", &var1);`会在终端中提供一个空行以供输入，并将“输入”赋值给var1，
					- 类似printf，scanf函数接受的主要*参数*仍然只是*单个字符串*（即"string"），
					- 应注意双引号“”和*&符号*（作为对比，printf中不需要&符号），
					- 输入字符串时*不需要*加入&符号，基本语法为`scanf("%s", str1);`，
				- 返回值
				  collapsed:: true
					- scanf的返回值为成功赋值的变量的个数（一般为正整数），可以赋值给int变量，
					- 若检测到的*输入类型*与占位符的类型不符合，则scanf不会读取输入并会返回数值0，
					- 若遇到其他错误，scanf会返回EOF值，通常被定义为-1，
				- 占位符
				  collapsed:: true
					- 类似printf函数，scanf函数和也需要利用占位符%来声明输入的变量的类型，
					- scanf函数所使用的占位符与printf相同，如%d代表整型数，%f代表浮点数，
					- 应注意char对应的占位符%c会将数值1表示为字符'1'，
				- 多个输入
				  collapsed:: true
					- scanf以空白（空格，换行符等）为分隔，将输入的字符串中以空白分隔开的字符逐个赋值给多个变量，
					- 如`scanf("%d %f", &var1, &var2);`会将`1 2`分别赋值给`var1 var2`，
						- scanf接受的字符串`"%d %f"`中用*空格*分隔多个变量，
						- scanf赋值时需要用*逗号*分别给变量赋值，
					- 由于scanf以空白（空格、换行符等）为分隔，因此scanf不会读取以空格分隔的整个字符串，而只会读取第一个词，
			- cin
			  collapsed:: true
				- syntax`cin >> var1 >> var2;`
				  collapsed:: true
					- behaves analogously to the output operator, but don't need explicit `endl`,
					- actually made of two input statement, `cin >> var1;`, `cin >> var2;`,
					- need variable declaration first,
					- input from command line is separated by blank(space, enter),
			- multiple inputs
				- fixed length
				  collapsed:: true
					- `cin` will automatically stop at blank(space, enter),
					- so that could set a loop and stops at N, or use `cin >> var1 >> var2 >>... >> varN;`(when N is small),
				- unknown length
				  collapsed:: true
					- stop by EOF
					  collapsed:: true
						- `while(cin >> var1){statements;}`,
						- this while loop will read multiple inputs separated by blank(space or enter),
						- stops until *EOF*(ctrl + d), or the data type doesn't match, blank(space or enter) *cannot* stop `istream`,
						- the value of var1 will be replaced by the latest input,
					- stop by `\n`
					- read with `getline`
			- `istream`
		- cerr(error)
		- clog(log)
	- file I/O
	  collapsed:: true
		- file redirection
- Template (polymorphism)
  collapsed:: true
	- (implementation inheritance)
	  collapsed:: true
		- an old design pattern that achieves *runtime* polymorphism through hierarchy of classes,
		- keyword `virtual`,
	- concept
		- designed for reusing the code with different *data types*,
		- a class or function with template parameters,
		- compiler will translate the template to different data types to achieve *compile*-time polymorphism,
	-
- Class
  collapsed:: true
	- `class` keyword
	  collapsed:: true
		- like `struct`in C, "groups" multi-variables into one variable,
		- C++'s `struct` can contain functions as well, and they are just as same as other functions,
		- classes declared with the `struct` and `class` keywords are nearly the *same*,
		  collapsed:: true
			- by default, `class`'s member are *private*, while `struct`'s member are *public*,
	- modular programming
	  collapsed:: true
		- for reusing, classes are always defined in a *single (header) file*, and usually names as `classes.h`,
		- first write the methods and comments about their behavior(input and output), instead of trying to finish all the code quickly,
	- concepts
	  collapsed:: true
		- data abstraction,
		- separate the interface and implementation,
		- different from struct, Class contains not only multi-variables, but also functions(methods) about these variables,
	- declaration
	  collapsed:: true
		- different from C, C++ allow giving *default* values of elements in struct,
		- like `struct student{std::string name; float height = 170.0;};`，
		- otherwise, these elements will have different default values according to their types, like `0` for`int` , `""`for `string`,
	- instances
	  collapsed:: true
		- using struct is similar to using other data types,
		- the syntax is `student TOM;`, like`int num;`,
		  collapsed:: true
			- `typedef` is implicitly omitted here, C's syntax is `struct student TOM` unless using `typedef struct student student`, while in C++, using `student TOM`directly is vaild,
		- initialization syntax is `student TOM = {"TOM", 171.0};`,
		  collapsed:: true
			- in C++, the `=` can be omitted,
			- members match from left to right, others will be set to default value,
	- @constructor
	  collapsed:: true
		- concept
		  collapsed:: true
			- functions used to initialize the data members of a class object, *working* when an *instance* is created,
		- definition
		  collapsed:: true
			- defining a constructor is optional, the compiler will *implicitly* define it, and the default behavior is to perform no action,
			- the constructor can be explicitly defined as well, and usually have *same name* with the class, like `student(parameters){statements;}`,
			- constructor is similar to other functions, and can have overloads,
		- @member initialization list
	- @destructor
	  collapsed:: true
		- concept
		  collapsed:: true
			- by contrast, used to destroy the data members of a class object,
		- definition
		  collapsed:: true
			- defining a destructor is optional, the compiler will *implicitly* define it, like constructor, the default behavior is to perform no action,
			- unlike constructor, destructor must have *no* parameters,
	- access control
	  collapsed:: true
		- private
		  collapsed:: true
			- `private: int A = 12;`will make member A inaccessible for *outside* approach(like `ST.A;`),
			- method's definition are similar,
		- public
	- elements (members)
	  collapsed:: true
		- dot method
		  collapsed:: true
			- elements in the struct could be approached through dot method, like `TOM.name;`,
		- arrow method
		  collapsed:: true
			- always used with pointers,
			- `datatype2 *spoint2; spoint2 = &data2;`，pointer initialization and assignment,
			- `spoint2 -> num3`, `(*spoint2).num3`and `data2.num3` are equal,
	- functions (methods)
	  collapsed:: true
		- general
		  collapsed:: true
			- methods' and members' order is not strict,
		- definition
		  collapsed:: true
			- pointer `this`
			  collapsed:: true
				- concept
				  collapsed:: true
					- methods access Class' members through a *pointer* named `this`, which is defined implicitly by the compiler,
					  id:: 63aeb962-5a8a-4921-815b-5e3d809f1d83
					- it's needless to explicitly use member access operators to fetch Class' member, while use arrow method is also valid `this->mem`,
				- using
				  collapsed:: true
					- resolve ambiguity
					  collapsed:: true
						- sometimes methods' parameter might have same name with members,
						- use `this->mem` with explicitly refer to the member of Class, instead of the parameter,
					- @return reference
					  collapsed:: true
						- using `this` is one way to return a reference to the Class,
						- the built-in assignment operator return a *lvalue*, thus return a *reference* is required,
						- so the return statement is `return *this;`,
			- member functions
			  collapsed:: true
				- methods can access members in the struct without using scope operator `::`,
				- `const` member functions
				  collapsed:: true
					- `this` is a const pointer that stores the address of the Class, but the struct itself is always not const, so that this might *change* the member of the struct,
					- to avoid that, one way is using `const` behind the parameter list, like`type func1() const {statements;}`,
					- this is similar to `type func1(const struct1 *const this){statements;}`,
			- member functions defined outside the Class
			  collapsed:: true
				- just define the prototype inside the struct, and the basic syntax is similar to common functions,
				- while the scope operator `::`is *required* in function *definition*(outside the struct), like `type struct1::func1() {statements;}`, but for function *statements*, using members don't need scope operator anymore,
			- non-member functions
			  collapsed:: true
				- function defined outside the struct can only use the struct itself, and not able to use the struct ' member directly,
				- and these functions are exactly not "methods" anymore, thus using them don't require dot method,
		- using
		  collapsed:: true
			- dot method
			  collapsed:: true
				- methods are also able to fetch through dot method,
				- parentheses() is required,like `mem.func1();`, even for methods that don't have arguments,
			- arrow method
			  collapsed:: true
				- always used with pointers,
	- inheritance
- @Debugging
  collapsed:: true
	- gdb
	  collapsed:: true
		- break points
		- info locals
	- exception
	  collapsed:: true
		- libraries
		  collapsed:: true
			- `<stdexcept>` header defines several general-purpose exception classes,
			  collapsed:: true
				- two main types, run-time error and logic error,
				- ![image.png](../assets/image_1667901533701_0.png)
			- `<exception>` header defines the most general kind of exceptions,
		- throw
		  collapsed:: true
			- syntax likes `throw runtime_error("error message");`,
			- `runtime_error` is a instance of exception class,
			- library function `terminate` will be called to end the program,
		- try-catch
		  collapsed:: true
			- syntax likes `try{statements1;} catch (error1 err){statements2;}catch (error2 err){statements3;}`,
			- when error appeared, compiler will search each `catch` to find the corresponding statement,
			- if no catch is appropriate, `terminate` will be called to end the program,
	- assert library
	  collapsed:: true
		- `assert` function
		  collapsed:: true
			- defined in header file `cassert`,
			- syntax like `assert(boolean;)`, will report error and terminate the program if the boolean value is false, and do nothing at the opposite,
			- often used to check extreme situations, such as the input value overflows,
			- (`assert` is not a reserved name in C++, while is recommended not to use `assert` as variable or function's name, )
		- `NDEBUG`
		  collapsed:: true
			- if preprocessor find the variable `NDEBUG`is defined(with `#define NDEBUG`), then the `assert` function won't be executed,
			- `NDEBUG` can also defined with command line, like `g++ -D NDEBUG file.c`,
- Header files
  collapsed:: true
	- preprocessor
	  collapsed:: true
		- runs before the compiler and changed the source code,
		- preprocessor functions are managed by preprocessor, so that it's not required to declare their namespace explicitly through `using`,
		  id:: 638320b6-bd82-41dc-902f-4a8dec66c657
	- header statements
	  collapsed:: true
		- header variables often written in ALL uppercase to avoid name crash,
		- `#define`
		- `#ifndef`and `#ifdef`
		  collapsed:: true
			- using to avoid multiple inclusion,
			- need to end with `#endif`,
		- Headers should not include using declarations to avoid unexpected name conflicts,
	- `extern` keyword
	- C library
	  collapsed:: true
		- C++ include all C libraries, and has two version like `<cstring>` and `<string.h>`,
		- the content of two file are same, but it's better to use `<cstring>`,
		- one reason is the names defined in the cname headers are defined inside the std namespace, whereas those defined in the .h versions are not,
-
- [[tools]]
- [[C]]
- [[Science]]