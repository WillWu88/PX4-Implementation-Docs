# C++ Development Notes

### Libraries
1. Static
	- linked at compile time
	- faster than shared libraries
	- linked as the last step of compilation
	- bigger than shared libraries
	- executable needs to be recompiled
	- no compatibility issue
2. Shared
	- linked at run time, managed by the operating system
	- smaller in size
	- potential compatibility issue
3. Module
	- more notes on this later

### Return Type
1. Return by value
	- like the name suggests
	- equally fast as return by reference thanks to return value optimization by compiler
	- safest 
	- fastest
2. Return by reference
	- can cause data hazard by return reference to local (out of scope) variable
	- can be used on the left side of operator
3. Return by pointer
	- can cause data hazard

### Macros

## References:
- [Libraries](https://www.geeksforgeeks.org/difference-between-static-and-shared-libraries/)
- [[Testing]] for C++ Unit Tests
- [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html#Function_Names) for naming conventions
#development 