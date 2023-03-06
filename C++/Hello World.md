# Hello World

Print Cheatsheet



TOPICS

Hello World[Variables](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-variables/cheatsheet)[Conditionals & Logic](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-conditionals-and-logic/cheatsheet)[Loops](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-loops/cheatsheet)[Loops Challenge Project](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-loops-challenge-projects/cheatsheet)[Vectors](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-vectors/cheatsheet)[Functions](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-functions/cheatsheet)[Functions Challenge Project](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-functions-challenge-projects/cheatsheet)[Classes & Objects](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-classes-and-objects/cheatsheet)[References & Pointers](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-references-and-pointers/cheatsheet)

### New Line

The escape sequence `\n` (backward slash and the letter n) generates a new line in a text string.

```
std::cout << "Hello\n";
std::cout << "Hello again\n";
```

### Program Structure

The program runs line by line, from top to bottom:

- The first line instructs the compiler to locate the file that contains a library called `iostream`. This library contains code that allows for input and output.
- The `main()` function houses all the instructions for the program.

```
#include <iostream>
 
int main() {
 
  std::cout << "1\n";
  std::cout << "2\n";
  std::cout << "3\n";
 
}
```

### Basic Output

`std::cout` is the “character output stream” and it is used to write to the standard output. It is followed by the symbols `<<` and the value to be displayed.

```
std::cout << "Hello World!\n"; 
```

### Compile Command

Using GNU, the compilation command is `g++` followed by the file name. Here, the name of the source file is **hello.cpp**.

```
g++ hello.cpp
```

### Execute Command

The execution command is `./` followed by the file name. Here, the name of the executable file is **a.out**.

```
./a.out
```

### Single-line Comments

Single-line comments are created using two consecutive forward slashes. The compiler ignores any text after `//` on the same line.

```
// This line will denote a comment in C++
```

### Multi-line Comments

Multi-line comments are created using `/*` to begin the comment, and `*/` to end the comment. The compiler ignores any text in between.

```
/* 
This is all commented out.
None of it is going to run!
*/
```
