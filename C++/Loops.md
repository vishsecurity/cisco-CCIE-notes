# Loops

Print Cheatsheet



TOPICS

[Hello World](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-hello-world/cheatsheet)[Variables](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-variables/cheatsheet)[Conditionals & Logic](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-conditionals-and-logic/cheatsheet)Loops[Loops Challenge Project](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-loops-challenge-projects/cheatsheet)[Vectors](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-vectors/cheatsheet)[Functions](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-functions/cheatsheet)[Functions Challenge Project](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-functions-challenge-projects/cheatsheet)[Classes & Objects](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-classes-and-objects/cheatsheet)[References & Pointers](https://www.codecademy.com/learn/learn-c-plus-plus/modules/learn-cpp-references-and-pointers/cheatsheet)

### `while` Loop

A `while` loop statement repeatedly executes the code block within as long as the condition is `true`. The moment the condition becomes `false`, the program will exit the loop.

Note that the `while` loop might not ever run. If the condition is `false` initially, the code block will be skipped.

```
while (password != 1234) {
 
  std::cout << "Try again: ";
  std::cin >> password;
 
}
```

### `for` Loop

A `for` loop executes a code block a specific number of times. It has three parts:

- The initialization of a counter
- The continue condition
- The increment/decrement of the counter

This example prints 0 to 9 on the screen.

```
for (int i = 0; i < 10; i++) {
  
  std::cout << i << "\n";
  
}
```
