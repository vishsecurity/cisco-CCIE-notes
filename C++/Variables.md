# Variables

Print Cheatsheet



TOPICS

[Hello World](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-hello-world/cheatsheet)Variables[Conditionals & Logic](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-conditionals-and-logic/cheatsheet)[Loops](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-loops/cheatsheet)[Loops Challenge Project](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-loops-challenge-projects/cheatsheet)[Vectors](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-vectors/cheatsheet)[Functions](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-functions/cheatsheet)[Functions Challenge Project](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-functions-challenge-projects/cheatsheet)[Classes & Objects](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-classes-and-objects/cheatsheet)[References & Pointers](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-references-and-pointers/cheatsheet)

### User Input

`std::cin`, which stands for “character input”, reads user input from the keyboard.

Here, the user can enter a number, press enter, and that number will get stored in `tip`.

```
int tip = 0;
 
std::cout << "Enter amount: ";
std::cin >> tip;
 
```

### Variables

A variable refers to a storage location in the computer’s memory that one can set aside to save, retrieve, and manipulate data.

```
// Declare a variable
int score;
 
// Initialize a variable
score = 0;
```

### Arithmetic Operators

C++ supports different types of arithmetic operators that can perform common mathematical operations:

- `+` addition
- `-` subtraction
- `*` multiplication
- `/` division
- `%` modulo (yields the remainder)

```
int x = 0;
 
x = 4 + 2;  // x is now 6
x = 4 - 2;  // x is now 2
x = 4 * 2;  // x is now 8
x = 4 / 2;  // x is now 2
x = 4 % 2;  // x is now 0
```

### `int` Type

`int` is a type for storing integer (whole) numbers. An integer typically requires 4 bytes of memory space and ranges from -2³¹ to 2³¹.

```
int year = 1991;
int age = 28;
```

### `double` Type

`double` is a type for storing floating point (decimal) numbers. Double variables typically require 8 bytes of memory space.

```
double price = 8.99;
double pi = 3.14159;
 
```

### Chaining the Output

`std::cout` can output multiple values by chaining them using the output operator `<<`.

Here, the output would be `I'm 28.`

```
int age = 28;
 
std::cout << "I'm " << age << ".\n";
```

### `char` Type

`char` is a type for storing individual characters. Characters are wrapped in single quotes `'`. Characters typically require 1 byte of memory space and range from -128 to 127.

```
char grade = 'A';
char punctuation = '?';
```

### `string` Type

`std::string` is a type for storing text strings. Strings are wrapped in double quotes `"`.

```
std::string message = "good nite";
std::string user = "@sonnynomnom";
 
```

### `bool` Type

`bool` is a type for storing `true` or `false` boolean values. Booleans typically require 1 byte of memory space.

```
bool organ_donor = true;
bool late_to_work = false;
```
