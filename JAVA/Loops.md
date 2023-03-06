# Loops

Print Cheatsheet



TOPICS

[Hello World](https://www.codecademy.com/learn/learn-java/modules/learn-java-hello-world/cheatsheet)[Variables](https://www.codecademy.com/learn/learn-java/modules/learn-java-variables/cheatsheet)[Object-Oriented Java](https://www.codecademy.com/learn/learn-java/modules/learn-java-object-oriented-java-u/cheatsheet)[Conditionals and Control Flow](https://www.codecademy.com/learn/learn-java/modules/learn-java-conditionals-control-flow-u/cheatsheet)[Arrays and ArrayLists](https://www.codecademy.com/learn/learn-java/modules/learn-java-arrays-and-arraylists/cheatsheet)Loops[String Methods](https://www.codecademy.com/learn/learn-java/modules/learn-java-string-methods/cheatsheet)[Access, Encapsulation, and Static Methods](https://www.codecademy.com/learn/learn-java/modules/java-access-encapsulation-and-static-methods/cheatsheet)[Inheritance and Polymorphism](https://www.codecademy.com/learn/learn-java/modules/learn-java-inheritance-and-polymorphism/cheatsheet)[Debugging](https://www.codecademy.com/learn/learn-java/modules/learn-java-debugging/cheatsheet)[Two-Dimensional Arrays](https://www.codecademy.com/learn/learn-java/modules/java-two-dimensional-arrays/cheatsheet)

### For-each statement in Java

In Java, the `for-each` statement allows you to directly loop through each item in an array or `ArrayList` and perform some action with each item.

When creating a `for-each` statement, you must include the `for` keyword and two expressions inside of parentheses, separated by a colon. These include:

1. The handle for an element we’re currently iterating over.
2. The source array or `ArrayList` we’re iterating over.

```
// array of numbers
int[] numbers = {1, 2, 3, 4, 5};
 
// for-each loop that prints each number in numbers
// int num is the handle while numbers is the source array
for (int num : numbers) {  
    System.out.println(num);
}
```
