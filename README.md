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

## 8. What is the main characteristic of the String class?
<details>
  <summary>Short Answer</summary>

This class(String) is non-modifiable
</details>

<details>
  <summary>Less Short Answer</summary>

There is no way to modify an instance of the string class that one it has been created so if you call `.toUpperCase()`, it does not change a string, it creates a new strings that holds the results. If you really want a string of characters that you can modify then you can use a specific class called `StringBuilder`. It's not a string it actually wraps an array of chars or bytes you can modify the content of this array and you can create a string from it by calling `toString()` on it.

One last word, you use a plus(`+`) to concatenate strings, forget about using the old string builder pattern, it's useless well most of the time
</details>

## 9. What is the difference between equally call(==) and equals
<details>
  <summary>Short Answer</summary>

Equally called(==) compare the references and equals calls a method
</details>

<details>
  <summary>Less Short Answer</summary>

If you compare strings with equal equal(==) you may get the answer false even if the strings have the same value. In a nutshell equal equal(==) is good to compare things that are not objects, int, long and alike.

You should never compare floats or double with equal equal(==) when you need to compare Floats or Double, what you should be doing is compute the absolute value of their differences and check if it is lesser than a very small value.

One last thing everything is a reference in Java so most of the time calling equal equal(==)  on object is wrong
</details>

## 10. What is the relationship between equals() and hashCode()
<details>
  <summary>Short Answer</summary>

Java specification says, if two objects are equals then they should have the same `hashCode`
</details>

<details>
  <summary>Less Short Answer</summary>

It means that when you override `equals()` then you should always override `hashCode()` as well. The Java spec says two objects that are equals must have the same hash code but the contrary is not true, you can have two objects with the same hash code but that are different. One last thing always use your IDE to write these methods, first your IDE, do not forget to override both methods and second it will give you a better implementation than the one you will write well most of the time
</details>

## 11. How can you duplicate an array?
<details>
  <summary>Short Answer</summary>

You have two solutions `Arrays.copyOf()` and `System.arrayCopy()`
</details>

<details>
  <summary>Less Short Answer</summary>

You have a clone method on Arrays `array.clone()` internally it returns an object that is cast to the right type so performance wise it's not ideal. Both `Arrays.copyOf()` and `System.arrayCopy()` need a destination array in which they copy your source array. `Arrays.copyOf()` of can truncate your source array if it's bigger than the destination array or can add it if it's smaller. `System.arrayCopy()` has a richer API. It can copy a portion of your source array in the destination array. One last word, `Arrays.copyOf()` calls `System.arrayCopy()` internally, so you can use the one you prefer
</details>

## 12. how can you reverse a String?
<details>
  <summary>Short Answer</summary>

  Wrap it in a `StringBuilder` and call `reverse()`
</details>

<details>
  <summary>Less Short Answer</summary>

  The string class is non-modifiable, so you cannot change what the string is. All you can do is create another string and that is the reverse of the first one. Looping over the letters of your string to reverse it is actually what the reverse method from `StringBuilder` is doing so don't bother re-inventing the wheel it's there for you to use it. 
  
  StringBuilder is a modifiable class so the letters are reversed internally. One last word to get the reversed string, you just need to call `toString()` on your StringBuilder object
</details>

## 13. What is the functional interface?
<details>
  <summary>Short Answer</summary>

An interface with only one abstract method
</details>

<details>
  <summary>Less Short Answer</summary>

Functional interfaces can be implemented with `Lambda Expressions`. Java is a statically typed language so all your variables have a type and all these types are known at compile time. The type of a Lambda is always a functional interface, no exception. A functional interface can contain any number of default all static methods it can have any method from the object class as abstract methods and only one abstract method that is the one that your Lambda has to implement.

One last word you can add the `@FunctionalInterface` annotation on your interface the compiler will then tell you if you got it right or not
</details>

## 14. What is the difference between overriding and overloading?
<details>
  <summary>Short Answer</summary>

`overriding` has to do with inheritance, `overloading` does not
</details>

<details>
  <summary>Less Short Answer</summary>

`Overloading` is the same method with different parameters, `overriding` is the redefinition of a method from a superclass in a subclass. When your code calls a method with different overloads, the compiler decides which method to call so overloading is result at compile time. This is called early binding and Overriding is not. The compiler cannot resolve the call, it is result at runtime this is called late binding. One last word you can prevent a method from being overridden by declaring it final with the `final` keyword, you cannot prevent the method from having different overloads
</details>

## 15. What is a map?
<details>
  <summary>Short Answer</summary>

`Map is an interface`

An object that maps keys to values
</details>

<details>
  <summary>Less Short Answer</summary>

Map is an interface from the `collections` framework, it's canonical implementation is a `HashMap`. You cannot have duplicates among the keys of a map and a given key can map a single value. There is no concept of multi-map in the `collections` framework where a key can be bound to several value, but you can map a key to a list of values. Only use non-modifiable objects for your keys small strings a few characters are enough or longer prefer them over integers even for small values. One last word the `HashMap` class supports null keys and null values but please don't do that, it will put you in trouble
</details>

## 16. What is an ArrayList?
<details>
  <summary>Short Answer</summary>

An implementation of the list interface backed by an array
</details>

<details>
  <summary>Less Short Answer</summary>

ArrayList is sometimes called the dynamic array because when the internal array of an ArrayList becomes full, it is transparently copied in a larger array. Be careful though because this array can only grow, it never shrinks so when all the ArrayList can become really fat in your application and eat up a lot of memory. One last thing ArrayList is your best choice for list implementation forget about linked list. LinkedLists are good for Stacks, we'll talk more on that another time
</details>

## 17. What is Finally? & Explain Finally?
<details>
  <summary>Short Answer</summary>

`Finally` marks a block after a try block that is always executed when the try block exits
</details>

<details>
  <summary>Less Short Answer</summary>

Always means even if there is a return, a continue, a break or an exception that causes the try block to exit. The finally block is the key tool to properly clean up resources that are not `Auto Closable` your best choice to open an auto closable resource is the try with resources statement because it takes care of the closing of this resource for you. Resources that are not Auto closable should be released in a finally block that's the case for `ReentrantLock` for instance or for `Semaphores`. One last word in case of a return in the try block the finally block is evaluated after the return

```java
class Scratch {
    public static void main(String[] args) {
        System.out.println("average = " + age());
    }
    private static int age() {
        try {
            return 1;
        } finally {
            return 2;
        }
    }
}
// average = 2
```
</details>

## 18. How to make a class immutable?
<details>
  <summary>Short Answer</summary>

Use `records` if you can
</details>

<details>
  <summary>Less Short Answer</summary>

If you cannot use record, make all the fields of this class `final` and don't forget to make this class `final` also because if you don't someone could add some mutable state to this class using inner returns and pass it around using polymorphism. Do not forget to make defensive copies of the modifiable objects you get as arguments in your Constructor like lists, maps and the alike and the same for your accessors make sure they do not leak references to your internal state that could be modifiable, use a defensive copy where you need it. One last thing String, Integer, Long and all the wrapper classes of the jdk are non-modifiable you can check them to see how they work
</details>

## 19. What is the difference between String and StringBuffer and StringBuilder?
<details>
  <summary>Short Answer</summary>

`String`is non-modifiable, `StringBuilder` is modifiable and `StringBuffer` is thread safe
</details>

<details>
  <summary>Less Short Answer</summary>

`StringBuffer` is rarely used. `StringBuilder` is nice for certain string manipulations like reversing a string or inserting a character.

Should you use string Builder to concatenate strings? Most of the time no if you're using Java 9 and later, string concatenation with plus has been optimized. If you're using Java 8 then in many cases concatenation with plus is in fact compiled with `StringBuilder`

One last word if you are joining string elements from a list or an array consider using `String.join()` the `StringJoiner` class and the `Collectors.joining()` character
</details>

## 20. How to make a Singleton?
<details>
  <summary>Short Answer</summary>

One pattern, you use an `enum` with a single value
</details>

<details>
  <summary>Less Short Answer</summary>

The pattern that uses a class with a private Constructor, a private static field and a factory method that tests if the private field is new or not is more complex either non-thread safe or buggy or both, making it thread safe using a double check locking is also buggy. Just look for this bug on your favorite search engine. Using anonym is super simple, thread safe, guaranteed bug free at the jvm level and recommended by the best experts.

One last word this any based pattern is used in many places in the jdk, you can check the source code of the `Comparator.naturalOrder()` factory method for example
</details>

## 21. What is a static method?
<details>
  <summary>Short Answer</summary>

A method declared with the `static` keyword
</details>

<details>
  <summary>Less Short Answer</summary>

A method that you can invoke without creating any object. You can invoke a static method with a class name, you can even invoke a static method through a null object. A static method cannot call a `non-static` method from the same class. Static methods are useful to implement processors or computations some classes only have static methods like Math, Arrays or Collections.

One last word, static methods are sometimes called Factory methods because they can be used to create objects in a certain way like `List.of()` that creates an empty list. Classes with only static methods are sometimes called Factory classes
</details>

## 22. How can you find a character in a String?
<details>
  <summary>Short Answer</summary>

There is a method for that called `indexOf()`
</details>

<details>
  <summary>Less Short Answer</summary>

The `string.indexOf()` method has several overloads, one just take a character in the form of an int, another char and int because Java supports Unicode and some characters cannot be encoded on a single char, another one takes a string because index of can also find small strings in bigger strings. Both can also take an index used to start the search from, indexOf returns the index or the first occurrence of the character or the string so if you want to find all the occurrences of a single letter you can loop in that way.

One last word is the character or the string is not found index of returns -1
</details>

## 23. What is a method reference?
<details>
  <summary>Short Answer</summary>

Another way of writing a Lambda expression
</details>
<details>
  <summary>Less Short Answer</summary>

There are four kinds of method references;
- `static method references`, this operator can be written in that way, and it also works with other types
  - ```java
    DoubleUnaryOperator op = d -> Math.sqrt(d);
    DoubleUnaryOperator op = d -> Math::sqrt;
    ```
- `bound method references`, the classical `System.out::println` is a bound method reference
  - ```java
    Consumer<String> c = s -> System.out.println(s);
    Consumer<String> c = System.out::println;
    ```
- `unbound method references`, are they may look like static calls like this one, but they are not so be careful
  - ```java
    ToIntFunction<String> f = s -> s.length();
    ToIntFunction<String> f = String::length;
    ```
- `constructor method references` like this one
  - ```java
    Supplier<List<String>> sup = () -> new ArrayList<>();
    Supplier<List<String>> sup = () -> ArrayList::new;
    ```
One last word to translate a method reference to Lambda, you need to know its exact type. One very last word method references are there to improve the readability of your code so if you feel your code is actually less readable with them don't use them
</details>

## 24. What is the default method?
<details>
  <summary>Short Answer</summary>

It's a regular method written in an interface

`Default method = Concrete methods in an interface`
</details>
<details>
  <summary>Less Short Answer</summary>

Default methods have been added to the language in Java 8.

`Java 7: no default methods`

Prior to that all the methods in an interface had to be `abstract` so the abstract keyword for abstract methods is not mandatory in interfaces, for regular concrete methods you need to add the default keyword thus their name default method. Apart from that default methods are just regular methods. A default method from an interface can be used by any object that implements that interface, and they can be overridden in any concrete class.

One last word in Java 8 default methods can only be `public` starting with Java 9 they can also be `private`
</details>

## 25. What does JIT mean?
<details>
  <summary>Short Answer</summary>

JIT stands for `Just In Time Compiler`
</details>
<details>
  <summary>Less Short Answer</summary>

What you have in a class file is the byte code of your class, this bytecode is first interpreted by your Java virtual machine. Running your Java code in that way is super slow so a first JIT compiler called `C1` compares it to machine language. The C1 compiler does a nice job but your compiled code can be optimized even further. That's the job of a second JIT compiler `C2`. C2 carefully analyzes the way your code is running and compiles it again to leverage some more optimization.

One last word, if at some point C2 sees that it can do better it will de-optimize your code and optimize it again
</details>