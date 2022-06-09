# Cmake Notes

## Notes

### 1. Basic Syntax
```cmake
cmake_minimum_required(VERSION xxx) #recommended
```
- Setting variables
```cmake
set(Foo "quoted_arg") #quoted argument
set(Foo unquoted_arg) #unquoted
set(Foo "A B C") #1 quoted arg
set(Foo a b c) #3 unquoted arg
```
- Refer to variable
```cmake
command(${Foo})
command("${Foo}") #quoted
```
- Scope
	- change in child scope will not impact parent scope
	- variable set in current file will be visible to the current file, subdirectories' cmake files, included files' cmake files, and functions and macros invoked
	- "set" can change the value of a variable in parent scope:
```cmake
set(Foo 2 PARENT_SCOPE) #doesn't change the variable in current scope
```
	- Variables only come into scope after they are set
- Commands
	- command names are not case sensitive
	- command arguments are space separated and case sensitive
- Control flow:
	- [if](https://cmake.org/cmake/help/latest/command/if.html#command:if)
	- *foreach*
		- variable name is expanded before eval, so it can be used to construct names
```cmake
if(${${tfile}}_TEST_RESULT} MATCHES FAILED)
  message("Test ${tfile} failed.")
endif()
```

### 2. Key Concepts
- Targets
	- executables, libraries, utilities
	- refer to [[C++ Notes]] for different types of libraries
	- two useful commands
```cmake
add_library(name soure1|source2)
target_link_libraries(<target> ... <item> ...) 
#target is created by add_library or add_executable command
```
- Usage requirements
	- link calls will link all libraries called (linking 1 library will link all the libraries linked to that library)
	- 
## Appendix: Reference
- [Mastering CMake Book](https://cmake.org/cmake/help/latest/manual/cmake-commands.7.html)
- [Official Tutorial](https://cmake.org/cmake/help/book/mastering-cmake/)
- [CMake Variables Manual](https://cmake.org/cmake/help/latest/manual/cmake-variables.7.html#manual:cmake-variables(7))
- [CMake Commands](https://cmake.org/cmake/help/latest/manual/cmake-commands.7.html)

#development 