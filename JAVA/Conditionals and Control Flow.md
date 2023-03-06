# Conditionals and Control Flow

Print Cheatsheet



TOPICS

[Hello World](https://www.codecademy.com/learn/learn-java/modules/learn-java-hello-world/cheatsheet)[Variables](https://www.codecademy.com/learn/learn-java/modules/learn-java-variables/cheatsheet)[Object-Oriented Java](https://www.codecademy.com/learn/learn-java/modules/learn-java-object-oriented-java-u/cheatsheet)Conditionals and Control Flow[Arrays and ArrayLists](https://www.codecademy.com/learn/learn-java/modules/learn-java-arrays-and-arraylists/cheatsheet)[Loops](https://www.codecademy.com/learn/learn-java/modules/learn-java-loops/cheatsheet)[String Methods](https://www.codecademy.com/learn/learn-java/modules/learn-java-string-methods/cheatsheet)[Access, Encapsulation, and Static Methods](https://www.codecademy.com/learn/learn-java/modules/java-access-encapsulation-and-static-methods/cheatsheet)[Inheritance and Polymorphism](https://www.codecademy.com/learn/learn-java/modules/learn-java-inheritance-and-polymorphism/cheatsheet)[Debugging](https://www.codecademy.com/learn/learn-java/modules/learn-java-debugging/cheatsheet)[Two-Dimensional Arrays](https://www.codecademy.com/learn/learn-java/modules/java-two-dimensional-arrays/cheatsheet)

### if-then-else

In Java, an *if-then-else statement* controls the execution of code by providing to execute when the value in the if-then statement is `false`.

```
boolean condition1 = true;
if (condition1){
    System.out.println("condition1 is true");
}
else{
    System.out.println("condition1 is not true");
}
// Prints: condition1 is true
```

### if-then statement

An *if-then statement* executes a block of code when a specified boolean expression is evaluated as `true`.

```
if (true) {
    System.out.println("This code executes");
}
// Prints: This code executes
 
if (false) {
    System.out.println("This code does not execute");
}
// There is no output for the above statement
```

### Nested Conditional Statements

A nested conditional statement is a conditional statement nested inside of another conditional statement. The outer conditional statement is evaluated first; if the condition is `true`, then the nested conditional statement will be evaluated.

```
boolean studied = true;
boolean wellRested = true;
 
if (wellRested) {
  System.out.println("Best of luck today!");  
  if (studied) {
    System.out.println("You are prepared for your exam!");
  } else {
    System.out.println("Study before your exam!");
  }
}
 
// Prints: Best of luck today!
// Prints: You are prepared for your exam!
```

### Conditional Operators - Order of Evaluation

If an expression contains multiple conditional operators, the order of evaluation is as follows: Expressions in parentheses -> NOT -> AND -> OR.

```
boolean foo = true && (!false || true); // true
/* 
(!false || true) is evaluated first because it is contained within parentheses. 
 
Then !false is evaluated as true because it uses the NOT operator. 
 
Next, (true || true) is evaluation as true. 
 
Finally, true && true is evaluated as true meaning foo is true. */
```
