# Java Coding Tips

## 1. What is Java?
<details>
  <summary>Short Answer</summary>

A programming language
</details>

<details>
  <summary>Lesser Short Answer</summary>

An object-oriented programming language with some lists of functional programming in it and actually more and more. Object-oriented programming means four things abstraction, capsulation, inheritance and polymorphism that Java supports all that. One restriction though it does not support multiple linear returns meaning that one class can only extend one other class. And I have a last one for you Java is a statically typed language meaning that the type of any variable you create or receive is known ad compiled timer even if you define the type with vowel the compiler will guess the type of this variable for you
</details>

## 2. What is the Object class in Java?
<details>
  <summary>Short Answer</summary>
  
The super class of every class you can create
</details>

<details>
  <summary>Less Short Answer</summary>

When you create a class you can explicitly extend another class with the extends keyword you can even declare that you extend the object class this is fine it's dumb because you don't need it but it's legal.
  
Remember a class can only extend one class in Java, multiple linear returns is not allowed. If you do not declare that your class extends anything which is fine then the compiler will make your class extend the object class for you so in the end every class in Java extends the object class
</details>

## 3. Can you cite methods from the object class?
<details>
  <summary>Short Answer</summary>

toString(), equals() and hashCode()
</details>

<details>
  <summary>Less Short Answer</summary>

There are more. getClass() gives you the class of the subject wait(), notify() and notifyAll(). These are used in concrete programming and never call these methods unless you really know what you're doing here. Finalize(), that one you should not override it anymore because it is deprecated and whatever you put in this method is most of the time buggy, most of the time, and the last one is cloner same stay away from this method so in a nutshell toString(), equals() and  hashCode() these are the most used ones
</details>

## 4. What are the differences between String and array of chars (char[])
<details>
  <summary>Short Answer</summary>

String is an object with many useful methods, An array only has methods from object and they are not very useful
</details>

<details>
  <summary>Less Short Answer</summary>

- String is a class with useful methods that chat[] has not
- String is non-modifiable

String of character is non-modifiable in Java, once you've created one you cannot modify it. The size of an array is fixed once created you cannot add elements to it, but you can replace one element by another.

How can you compare string? Just use their equals() method, trying to compare an array with its `equals()` method doesn't do what you would expect. You need to use `equals()` from the arrays Factory class(`Arrays.equals()`) and the same goes for the `toString()` method you need to use `toString()` from the same arrays factory class(`Arrays.toString()`) to properly print an array.

One last word, you can create a string a prominent array of chars by calling `new String()` and passing this array as an argument

```java
char[] letters = {'h', 'e', 'l', 'l', 'o'};
String hello = new String(letters);
```

</details>

## 5. How do you sum the elements of an array
<details>
  <summary>Answer</summary>

Two solutions are, a dumb one & old-fashioned that everyone knows, and a great one

- The first one iterate over the array, add the elements to the sum variable, don't forget to set it to zero at the start and you're done and the result is 10.
  - ```java
    int[] ints = {0, 1, 2, 3, 4};
    int sum = 0;
    for (int element: ints) {
        sum += element;
    }
    System.out.println("sum = " + sum); // sum = 10
    ``` 
- The second one, make your stream from your array and just call `sum()`, of course the result is the same and by the way you can also call `min()`, `max()` and `average()` on the stream. Yes this is the one I prefer, it's simpler cleaner and more readable
  - ```java
    import java.util.Arrays;

    int[] ints = {0, 1, 2, 3, 4};
    int sum = Arrays.stream(ints).sum();
    System.out.println("sum = " + sum); // sum = 10
    double average = Arrays.stream(ints).average().orElseThrow();
    System.out.println("average = " + average); // average = 2.0
    ``` 
</details>

## 6. What is the JVM?
<details>
  <summary>Short Answer</summary>

Java virtual machine
</details>

<details>
  <summary>Lesser Short Answer</summary>

The piece of software that can run your Java code. The JVM does many things for you besides running your application among many other things. It handles the memory of your application with an element called the `Garbage Collector` or `GC`. It optimizes the code that you're running with another element called the `Just In Time` compiler or `JIT` and it handles the security of your application making sure that no undesired code can sneak in and be executed on your behalf. One last word if someone talks to you about hotspot that's the name of the open sourced jvm developed by defaults at the Open JDK.
</details>

## 7. How can you sort an array?
<details>
  <summary>Short Answer</summary>

There is a method for that called `Arrays.sort(tab)` that's all. Pass your retreat and that's it.
</details>

<details>
  <summary>Less Short Answer</summary>

When you need to sort something, forget about writing a sort algorithm yourself. What about the best sorting algorithm that's actually a tough question but you don't need to worry about that because a `Arrays.sort(...)` does the job for you. Now if you really want to shine during an interview, you can cite three algorithms, `QuickSort`, `HeapSort` and `TimSort`.

The one used in a `Arrays.sort(...)` is called `dual pivot quicksort`. One last word never cite `BubbleSort` unless you want to say that it's a terrible algorithm
</details>