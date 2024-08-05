# Cracking the Java Coding Interview

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

The piece of software that can run your Java code. The JVM does many things for you besides running your application among many other things. It handles the memory of your application with an element called the `Garbage Collector` or `GC`. It optimizes the code that you're running with another element called the `Just In Time` compiler or `JIT` and it handles the security of your application making sure that no undesired code can sneak in and be executed on your behalf.

One last word, if someone talks to you about hotspot that's the name of the open sourced jvm developed by defaults at the Open JDK.
</details>

## 7. How can you sort an array?
<details>
  <summary>Short Answer</summary>

There is a method for that called `Arrays.sort(tab)` that's all. Pass your retreat and that's it.
</details>

<details>
  <summary>Less Short Answer</summary>

When you need to sort something, forget about writing a sort algorithm yourself. What about the best sorting algorithm that's actually a tough question but you don't need to worry about that because a `Arrays.sort(...)` does the job for you. Now if you really want to shine during an interview, you can cite three algorithms, `QuickSort`, `HeapSort` and `TimSort`.

The one used in a `Arrays.sort(...)` is called `dual pivot quicksort`.

One last word, never cite `BubbleSort` unless you want to say that it's a terrible algorithm
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

You have a clone method on Arrays `array.clone()` internally it returns an object that is cast to the right type so performance wise it's not ideal. Both `Arrays.copyOf()` and `System.arrayCopy()` need a destination array in which they copy your source array. `Arrays.copyOf()` of can truncate your source array if it's bigger than the destination array or can add it if it's smaller. `System.arrayCopy()` has a richer API. It can copy a portion of your source array in the destination array.

One last word, `Arrays.copyOf()` calls `System.arrayCopy()` internally, so you can use the one you prefer
</details>

## 12. how can you reverse a String?
<details>
  <summary>Short Answer</summary>

  Wrap it in a `StringBuilder` and call `reverse()`
</details>

<details>
  <summary>Less Short Answer</summary>

The string class is non-modifiable, so you cannot change what the string is. All you can do is create another string and that is the reverse of the first one. Looping over the letters of your string to reverse it is actually what the reverse method from `StringBuilder` is doing so don't bother re-inventing the wheel it's there for you to use it. 
  
StringBuilder is a modifiable class so the letters are reversed internally.
  
One last word to get the reversed string, you just need to call `toString()` on your StringBuilder object
</details>

## 13. What is the functional interface?
<details>
  <summary>Short Answer</summary>

An interface with only one abstract method
</details>

<details>
  <summary>Less Short Answer</summary>

Functional interfaces can be implemented with `Lambda Expressions`. Java is a statically typed language so all your variables have a type and all these types are known at compile time. The type of a Lambda is always a functional interface, no exception. A functional interface can contain any number of default all static methods it can have any method from the object class as abstract methods and only one abstract method that is the one that your Lambda has to implement.

One last word, you can add the `@FunctionalInterface` annotation on your interface the compiler will then tell you if you got it right or not
</details>

## 14. What is the difference between overriding and overloading?
<details>
  <summary>Short Answer</summary>

`overriding` has to do with inheritance, `overloading` does not
</details>

<details>
  <summary>Less Short Answer</summary>

`Overloading` is the same method with different parameters, `overriding` is the redefinition of a method from a superclass in a subclass. When your code calls a method with different overloads, the compiler decides which method to call so overloading is result at compile time. This is called early binding and Overriding is not. The compiler cannot resolve the call, it is result at runtime this is called late binding.

One last word you can prevent a method from being overridden by declaring it final with the `final` keyword, you cannot prevent the method from having different overloads
</details>

## 15. What is a map?
<details>
  <summary>Short Answer</summary>

`Map is an interface`

An object that maps keys to values
</details>

<details>
  <summary>Less Short Answer</summary>

Map is an interface from the `collections` framework, it's canonical implementation is a `HashMap`. You cannot have duplicates among the keys of a map and a given key can map a single value. There is no concept of multi-map in the `collections` framework where a key can be bound to several value, but you can map a key to a list of values. Only use non-modifiable objects for your keys small strings a few characters are enough or longer prefer them over integers even for small values.

One last word, the `HashMap` class supports null keys and null values but please don't do that, it will put you in trouble
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

Always means even if there is a return, a continue, a break or an exception that causes the try block to exit. The finally block is the key tool to properly clean up resources that are not `Auto Closable` your best choice to open an auto closable resource is the try with resources statement because it takes care of the closing of this resource for you. Resources that are not Auto closable should be released in a finally block that's the case for `ReentrantLock` for instance or for `Semaphores`.

One last word, in case of a return in the try block the finally block is evaluated after the return

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

One last word, if you are joining string elements from a list or an array consider using `String.join()` the `StringJoiner` class and the `Collectors.joining()` character
</details>

## 20. How to make a Singleton?
<details>
  <summary>Short Answer</summary>

One pattern, you use an `enum` with a single value
</details>

<details>
  <summary>Less Short Answer</summary>

The pattern that uses a class with a private Constructor, a private static field and a factory method that tests if the private field is new or not is more complex either non-thread safe or buggy or both, making it thread safe using a double check locking is also buggy. Just look for this bug on your favorite search engine. Using anonym is super simple, thread safe, guaranteed bug free at the jvm level and recommended by the best experts.

One last word, this any based pattern is used in many places in the jdk, you can check the source code of the `Comparator.naturalOrder()` factory method for example
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

One last word, is the character or the string is not found index of returns -1
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
One last word, to translate a method reference to Lambda, you need to know its exact type. One very last word method references are there to improve the readability of your code so if you feel your code is actually less readable with them don't use them
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

One last word, in Java 8 default methods can only be `public` starting with Java 9 they can also be `private`
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

## 26. What kind of method can you override?
<details>
  <summary>Short Answer</summary>

Instance methods
</details>
<details>
  <summary>Less Short Answer</summary>

`static` methods cannot be overridden because you call them using an explicit class name so even if a Class B extends a Class A and defines the same static method you can still call each of them. Instance method can be overridden as long as they are non-private, non-final and that their class can be extended. The obvious way to prevent a class from being extended is to make it `final`, but you can also declare it's NoArgConstructor private.

`Safe way: copy the method declaration`

One last word, the safest way to override a method, just to copy its declaration in your extending class with the written type, the parameters and the exceptions, but you can be more certain than that and that will be for another time
</details>

## 27. What is the signature of a method?
<details>
  <summary>Short Answer</summary>

Its name and its parameters
</details>
<details>
  <summary>Less Short Answer</summary>

Neither the return type of a method nor its declared exceptions are part of its signature because all the methods of a given class must have different signatures, you can have several methods with the same name as long as they have different parameters and these methods can have different written types, but it is not legal to have two methods with the same name, same parameters and just a different return type because they would have the same signature.

One last word, this rule holds even if one of this method is abstract because it would force the implementation to break this rule
</details>

## 28. What is a marker interface?
<details>
  <summary>Short Answer</summary>

An interface with no method that is just here to Mark a class
</details>
<details>
  <summary>Less Short Answer</summary>

Being a marker interface is not really a language or an API notion, it's just a way of describing the nature of some interfaces. There are several examples in the jdk of such interfaces serializable of course that allows the instance of a class to be serialized and the cloneable that allows instances of a class to be cloned.

One last thing, because there is no method in these interfaces you need to check if the object you have is an instance of this interface. It can be done with `instanceOf` or directly at the class level with the method is assignable from defined on the class of class
</details>

## 29. What is the difference between Collection and Set?
<details>
  <summary>Short Answer</summary>

There are no duplicate elements in the set
</details>
<details>
  <summary>Less Short Answer</summary>

`Collection` and `Set` are interfaces from the collections framework. `Set` extends collection all the instance method defined in the set interface override method from collection and are redefined to modify the semantic. They do not work in the same way. The set interface is implemented by `HashSet` which has another very interesting property, its implementation of the contain method is super fast, much faster than the one from arraylist.

One last word, if you need both the iterability property of arraylist and the fast container implementation you may take a look at the `LinkedHashSet` class which unfortunately is not released
</details>

## 30. How does finalize work?
<details>
  <summary>Short Answer</summary>

It does not work
</details>
<details>
  <summary>Less Short Answer</summary>

`finalize` has been deprecated in Java 9 and deprecated for removal in Java 18, so stop using it. `finalize` is supposed to be a method called by some undefined elements when the garbage collector detects that an object is not reachable anymore.

Here are two of the major issues with finalizer; first, the thread running finalized is not specified those are that you can get race conditions in this method. Second, it may take a lot of time for this method to be called, the correctness of your code should never rely on the fact that finalize is called.

One last word, there is a replacement pattern called `The Cleaner Pattern` you can check the cleaner class for more information
</details>

## 31. What are the main features of java 8?
<details>
  <summary>Short Answer</summary>

Lambda Expressions
</details>
<details>
  <summary>Less Short Answer</summary>

This version so Lambda expression added to the language but there are many other things that have been added to Java 8. The collections frameworks has been rewritten with many new features and methods. The stream API is a very clean implementation of map, filter, reduce that you can use in parallel. The completable future API is an asynchronous programming model added to the jdk and many many small things here and there to make your developer life better. 

One last word, Java 8 was released in March 2014 as of this recording that was 9 years ago if you're still working on this version, you should really consider moving to a more recent one
</details>

## 32. Do streams and collections have common methods?
<details>
  <summary>Short Answer</summary>

Yes and no, they do have one method that is called the same and take the same parameter
</details>
<details>
  <summary>Less Short Answer</summary>

This method is called `foreach`, it takes a consumer and you have it on both the stream interface and the iterable interface that being said even if they are basically doing the same thing, these methods are not implemented in the same way. Most of the time you can call directly `collections.foreach(...)` instead of calling `collections.stream().foreach()` that makes you save the creation of the stream object if you don't use it why would you want to create it.

```java
List<String> letters = List.of("h","e","l","l","o");
letters.forEach(System.out::println);

letters.stream().forEach(System.out::println);
```

One last word, even if collections and streams are there to process data there are many differences between them but that's for another time
</details>

## 33. How can you tell that a string is an anagram of another string?
<details>
  <summary>Short Answer</summary>

The easy way sort the letters of the strings and just compare them
</details>
<details>
  <summary>Less Short Answer</summary>

There is actually a much smarter way of doing that you can map each letter to prime number, for instance map A to 2, B to 3, C to 5 etc, then multiply all these numbers either two numbers you get are the same these strings are anagrams. It comes from the fact that the decomposition of an integer in a product of prime number is unique. The first method has a complexity of `n*log(n)` the second one is just `n` which is faster.

```
C -> 5
A -> 2
T -> 71
CAT -> 5*2*71 = 710
ACT- -> 2*5*71 = 710
```

One last word, be careful not to overflow when you're doing the multiplication it can happen for long strings of characters
</details>

## 34. On what kind of source can you build a streamer?
<details>
  <summary>Short Answer</summary>

There is no short answer, there are many sources
</details>
<details>
  <summary>Less Short Answer</summary>

You can create streams on the following;

Collections of course this is the most common way but the jdk offers much more than that because you can also create a stream on the lines of a text file on the characters of a string of characters. On the elements of a string you split using a regular expression and several others plus. The stream API gives you what you need to connect the stream on your own source of data.

- Collections and array
- Lines of a text files
- Regular expressions
- You can build your own

One last word, be careful that the processing of a stream should not modify its source while it is consuming it. If you do that then the result you will get is unpredictable
</details>

## 35. What is the groupingBy()?
<details>
  <summary>Short Answer</summary>

A collector, you can use to build maps that are in fact histograms from the elements of a stream
</details>
<details>
  <summary>Less Short Answer</summary>

The pattern is `stream().collect(...)` and pass `Collectors.groupingBy(...)` and then you need to pass a function to this groupingBy() this function maps each element of your stream to a key that is then added to your map. The corresponding element is itself added to a list bound to this key so if several elements of your streams are mapped to the same key you will find them together in this list.

```java
List<String> letters = List.of("h", "e", "l", "l", "o");
letters.stream().collect(Collectors.groupingBy(City::state))
```

One last word, you can post process this list with another character, pass as a second argument to this grouping by, this other character is called the downstream character
</details>

## 36. What is the difference between fifo and lifo?
<details>
  <summary>Short Answer</summary>

`FIFO` is a queue, `LIFO` is a stack
</details>
<details>
  <summary>Less Short Answer</summary>

`FIFO` stands for `F`irst `I`n `F`irst `O`ut and `LIFO` stands for `L`ast `I`n `F`irst `O`ut.

There are two interfaces in the jdk to model these, queue, that models the fifo that is extended by `deque` and that's the second interface that models will live for. The preferred implementation for both of these interfaces is `ArrayDeque` but it's not thread safe. If you need a thread safe implementation you can use a `ConcurrentLinkedQueue` for queue or `ConcurrentLinkedDeque` for deque.

One last word, there is a stack class in a jdk that is an extension of the vector class both `Stack` and `Vector` have been deprecated a long time ago, so you should not use them anymore
</details>

## 37. What is the GOF?
<details>
  <summary>Short Answer</summary>

The nickname of the fundamental book on design patterns
</details>
<details>
  <summary>Less Short Answer</summary>

The full title of this book is `Design patterns; Elements Of Reusable Object-Oriented Software`. it was published in 1994. The four authors are `Erich Gamma`, `Richard Helm`, `Ralph Johnson` and `John Vlissides`. This book contains a 23 design patterns in three categories; 

- Creational: with the Builder, the Factory of the Singleton
- Structural; with the Adapter, the Decorator of the Proxy
- Behavioral; with the Iterator the Strategy of the Visitor.

One last word, this book is a must read. The examples are written in C++ but it's easy enough to convert them to Java or to your favorite language
</details>

## 38. How can you create a Comparator?
<details>
  <summary>Short Answer</summary>

Just use the factory methods of the `Comparator` interface
</details>
<details>
  <summary>Less Short Answer</summary>

This interface has a bunch of factory methods to create comparators that compare objects using one of their fields, it also has default methods to modify the behavior of a given comparator for instance you can compare people using their last name and in case you have people with the same last name you can then compare them using their first name. In case you want to use this comparator to sort a list of people but need to sort them in the reverse order and then you can call reversed on an existing comparator.

```java
var userComparator = Comparator
        .comparing(User::lastName)
        .thenComparing(User::firstName)
        .reversed();
```

One last thing, null values are always painful to handle when you want to sort a list. The comparator interface has also a `nullsFirst` and `nullsLast`

```java
var userComparatorWithNullsFirst = Comparator.nullsFirst(userComparator);
var userComparatorWithNullsLast = Comparator.nullsLast(userComparator);
```
</details>

## 39. Can you cite functional interfaces that existed before Java 8?
<details>
  <summary>Short Answer</summary>

`Runnable`, `Comparator`, `Iterable`
</details>
<details>
  <summary>Less Short Answer</summary>

They are actually more, the definition of a functional interface is such that some existing interfacers became functional with Java 8. Because you can Implement a functional interface with a Lambda, it means that if you have old interfaces in your application that qualify for functional interfaces and then you can use lambdas to implement them without having to recompile them. That's why the `@FunctionalInterface` annotation is not mandatory on the functional interface.

One last word, you want more sure `Executor` even `Comparable` is a functional interface though I'm not sure that you want to implement this one with another expression
</details>

## 40. How can you open a file for writing some text?
<details>
  <summary>Short Answer</summary>

There is a factory method for that in the `Files` class
</details>
<details>
  <summary>Less Short Answer</summary>

There are actually two patterns; one from the old days of `java.io` and the less old one from java and IO and this is the one you should prefer. The exact pattern is the `Files.newBufferedWriter(...)` that takes a path as an argument, it has several overloads.

```java
var writer = Files.newBufferedWriter(
        path,
        StandardCharsets.ISO_8859_1,
        StandardOpenOption.CREATE,
        StandardOpenOption.APPEND
);
```

You can specify the Charsets used by your text file, the default value being utf-8 and you can specify some open options. Do you want to create the file if it does not exist and if it does do you want to erase its content or append to it.

One last word, what you get is still a buffered writer that you can still decorate if you need
</details>

## 41. What is the difference between a Sorted and an Ordered Collection?
<details>
  <summary>Short Answer</summary>

So that means that you can compare your elements, ordered means that you can access them using an index
</details>
<details>
  <summary>Less Short Answer</summary>

It has to do with how you can iterate over the elements of your collection. The sorted collection gives you the smallest element first up to the largest one. If you add an element to a sorted collection you may change the iteration order. An ordered collection on the other hand respects the order in which you add your elements so the first element is the first that has been added up to the last one.

One last word, ordered collections are modeled by the lists in the collection framework, your favorite implementation is a `ArrayList` and sorted collections are modeled by navigable set implemented by `TreeSet`
</details>

## 42. How can you open a file for reading binary data?
<details>
  <summary>Short Answer</summary>

There is a factory method for that on the `Files` class
</details>
<details>
  <summary>Less Short Answer</summary>

The all patterns from java 1.1 based on the decoration pattern are still there, but you should use the files Factory class to create your readers, writers, input stream and output stream.

```java
Files.newInputStream(path);
```

The implementations you will get are built on top of java and IO (`java.io`) and they are going to give you better performances. You can still use The Decorator pattern if you need to build data input stream or data output streamed, gzip streams or streams that mixed text and data. 

One last word, using the patterns from the files Factory class also give you final control on the opening of files on the `CharSet` you can use to read your text files and they are built to use the path object instead of file objects which is better
</details>

## 43. How can you print an array on the console?
<details>
  <summary>Short Answer</summary>

Use the factory method from the `Arrays` class

```java
Arrays.toString(array);
```
</details>
<details>
  <summary>Less Short Answer</summary>

An Array is an object but with a default to string method that you cannot override so printing it on the console directly gives you something that you do not want. You can call `Arrays.toString()` and pass your array it will print the content of your array on called toString() on each element of this array if it is an object. If you are not happy with the formatting you then need to iterate on the elements of this array or create a stream on it and create the strings of characters you need.

```java
var result = Arrays.stream(new String[]{"one", "two"})
        .map(Object::toString)
        .collect(Collectors.joining(",", "{", "}"));
System.out.println(result); // {one,two}
```

One last word, you can use arrays in the foreach pattern, this pattern works for any object that implements the `iterable` interface, now interval declares a foreach method, but you cannot call it on arrays
</details>

## 44. How does a SortedSet work?
<details>
  <summary>Short Answer</summary>

It is a set that keeps its elements sorted
</details>
<details>
  <summary>Less Short Answer</summary>

First point, it's a set so it doesn't have any duplicates if you add two elements that are equal then the second one will not be added. Second point the elements you add must be comparable or if they are not you must provide a comparator when you create your SortedSet. If you provide a comparator, it will be used even if your elements are comparable and when you iterate over them they will be sorted in the increasing order as of java 6 you should favor `NavigableSet` instead of SortedSet that gives you more method than total sets.

One last word, the default implementation is `TreeSet` which implements a red black tree
</details>

## 45. What pattern has been used to create the Java I/O API?
<details>
  <summary>Short Answer</summary>

The Decorator pattern
</details>
<details>
  <summary>Less Short Answer</summary>

The Decorator pattern is a `Structural Pattern` from the `Gang of Four` (GoF) book. A decorator is in fact a wrapper on an object that extends the class of that object, it may add more methods or change the way the existing methods are working. Wrapping an existing object means that it's Constructor takes an object of the superclass as a parameter so it is both `an extension` and `a composition` for instance `BufferedReader` extends reader and as the readline method, plus the reading works with a buffer.

One last word, you should use the `Files` factory class to build the base objects you need to read and write content to files, but you can still decorate them to add features to the base objects you get
</details>

## 46. What are the different categories of design patterns?
<details>
  <summary>Short Answer</summary>

Three categories; `Creational`, `Structural`, `Behavioral`
</details>
<details>
  <summary>Less Short Answer</summary>

It refers to the `Gang of Four` (GoF) book a must read for every developer. Some creational patterns; `Factory`, `Builder` and `Singleton`, some structural patterns; `Decorator`, `Facade`, `Proxy`, some behavioral patterns; `Iterator`, `Template Method` and a well-known `Visitor`. The GoF gives you C++ implementations, some of them are updated but the ideas are still excellent.

One last word, there are many patterns that are so widely used that you use them even if you don't know them. That's the case for the iterative pattern or the factory pattern
</details>

## 47. How can you count how many times a letter appears in a String?
<details>
  <summary>Short Answer</summary>

You need to iterate over the string in one way or another
</details>
<details>
  <summary>Less Short Answer</summary>

Two ways; first, you can look for your letter in a string with `indexOf()` until you don't find it anymore. `indexOf()` may take an index where it will start its search that's a quick and efficient pattern. Second pattern, you can stream on the letters of the stream removing the letters that do not match and count the result, efficient, more functional, more readable, this is the one I prefer.

One last word, the `count` method return the long that you can safely cast to an end. A string of character is backed by an array so there is no way you can have more than `Integer.MAX_VALUE` letters

```java
public void countLoop(String sentence, int letter) {
  int count = 0;
  int index = sentence.indexOf(letter);
  while (index >= 0) {
      count++;
      index = sentence.indexOf(letter, index + 1);
  }
  System.out.println(count);
}
public void countStream(String sentence, int letter) {
  long count = sentence.chars()
          .filter(c -> c == letter)
          .count();
  System.out.println(count);
}
```
</details>

## 48. What is a bucket in a Map?
<details>
  <summary>Short Answer</summary>

A cell in an array
</details>
<details>
  <summary>Less Short Answer</summary>

The HashMap class from the collections framework is backed by an array, when you add a key to a hashmap a special HashCode is evaluated for that key to choose which cell of the Array will receive the key value pair. It has already a different key value pair in this cell, this is called the `collision` and then a `LinkedList` is created to add this second pair and if there are too many, this LinkedList is actually replaced by your `Red Black Tree` to minimize collisions when the amount of key value pairs reaches `75%` of the size of the array then it is copied in a new larger array.

One last word, this copying incurs the re-hashing of all the keys present in a map which may be costly so be careful about that and try to create maps with the right size
</details>

## 49. What does Synchronized mean?
<details>
  <summary>Short Answer</summary>

It is a keyword that prevents more than one thread to execute a given block of code at the same time
</details>
<details>
  <summary>Less Short Answer</summary>

Synchronization has to do with concurrent programming, this block of code can be a delimited block inside the method or it can be the wall method static or not. All synchronized blocks need an object that they use as a key you can use the same key for more than one synchronized block. In the case of a synchronized method then the key is the object itself or the class if the method is static. There are limitations with synchronized block that you don't have with `ReentrantLock` so we can use these objects instead.

One last word, never expose your key or your locks. It will help you prevent `Deadlocks` a situation that you absolutely want to avoid
</details>

## 50. What is the difference between a Collection and a Stream?
<details>
  <summary>Short Answer</summary>

A collection contains an object, a stream is empty
</details>
<details>
  <summary>Less Short Answer</summary>

A collection is meant to carry objects around with methods to handle them, most of the time your stream is an empty object that you can connect to a source of objects to process them this source can be a collection, an array and many other things. You can even connect a stream to your own source of data if you need it. It will then process your elements one by one lazily. Some methods like `findAny()` or `allMatch()` can interrupt the processing of these objects.

One last word, there are actually two methods that need to remember the processed object; `distinct` and `sorted` so if you're using them then your stream will not be empty anymore
</details>

## 51. What is the difference between a File and a Path?
<details>
  <summary>Short Answer</summary>

A file is a class and the path is an interface
</details>
<details>
  <summary>Less Short Answer</summary>

The file class is from java 1.0 but is from java and IO released with Java 7. An instance of file is the same no matter what file system you're using because path is an interface the instance you build depends on the file system. You can get attributes that are specific to these file systems like security attributes as of now you should favor the use of path objects over file objects.

One last word, creating an instance of file all path does not create the corresponding file or directory on your disk, you need to call create new file on the file class or the `Files.createFile()` Factory method that takes a path as an argument to do that
</details>

## 52. What is the difference between a Checked and an Unchecked Exception?
<details>
  <summary>Short Answer</summary>

You need to write special code to handle the checked exception not for unchecked exceptions
</details>
<details>
  <summary>Less Short Answer</summary>

All your exceptions extend the `Exception.class` if an exception actually extends `Runtime` exception then it is an unchecked exception if it does not then it is checked exceptions. You need to handle your checked exceptions either by catching them or by declaring them in the `throws` clause of your methods and constructors. You do not need to do that for unchecked exceptions.

One last word, all these classes extend themselves the `Throwable.class` also extended by the `Error.class`. Errors are also unchecked exceptions but reserved for serious problems like Out Of Memory(OOM) error or Stack Overflow error
</details>

## 53. What is a Stream?
<details>
  <summary>Short Answer</summary>

An object that implements the `map`, `filter`, `reduce` pattern
</details>
<details>
  <summary>Less Short Answer</summary>

The stream consumes elements from a source and can do several operations these operations are organized in a pipeline where each element is passed from one step of the pipeline to the next one. Mapping an element consists in transforming it, filtering consists in deciding if this element should be transmitted or not based on a predicate and what you seeing may consist in many things summing the elements, extracting a min or a max or adding them to a list or a map.

One last word, the stream API allows you to conduct these computations in parallel, still you need to be careful with that as always when it comes to optimizations measure don't guess
</details>

## 54. What is the hash code of an object?
<details>
  <summary>Short Answer</summary>

A mapping of an object to an integer
</details>
<details>
  <summary>Less Short Answer</summary>

The idea behind the HashCode is to represent any object within it so that you can quickly tell if two objects are different by just comparing their Hash Code indeed the specification says that two objects that are equal must have the same as code but it turns out that two different objects may also have the same hash code so if two objects have different hash code then they cannot be equal but if they have the same hash code then you need to compare them to see if they are equal.

One last word, there are many ways of computing hash codes some are better than others if you're not sure on what you need relying on your IDE to generate the hash code method is probably your safest choice
</details>

## 55. What is an ExecutorService?
<details>
  <summary>Short Answer</summary>

An object to which you can submit tasks to be executed in another thread
</details>
<details>
  <summary>Less Short Answer</summary>

ExecutorService is an interface part of the `java.util.concurrent` API added to the `JDK 5` in 2004. It's the preferred way to run tasks in another thread in fact you shouldn't be creating threads by calling `new Thread()` anymore. A task can be either a `runnable` or `callable` that you can implement with a lambda expression submitting a task gives you a future object that you can use to get a result. An exception if something goes wrong all that you can use to interrupt the running of this task.

One last word, an executive service is sometimes called the `Pool Threads` and most of the time it is but it can also create threads on demand which is what it is doing for virtual threads for instance
</details>

## 56. What is an Iterator?
<details>
  <summary>Short Answer</summary>

An object used to iterate over the elements of a collection
</details>
<details>
  <summary>Less Short Answer</summary>

Iterator is an interface with three method; `hasNext()` that tells you if there are more objects to iterate over we should call this method first then if it returns, true you can call `next()` to get the next object and move the iterator one step it also has a `remove()` method that can throw an `UnsupportedOperationException` you need that if your collection is immutable. Most of the time you use iterators for collections but iterators can actually be created without them for instance you can create a `RangeIterator` that can iterate over a range of integers.

```java
import java.util.Iterator;

public class RangeIterator implements Iterator<Integer> {
    private int index = 0;
    
    public boolean hasNext() {
        return index < end;
    }
    public Integer next() {
        return index++;
    }
}
```

One last word, the iterator pattern is actually a pattern from the `Gang of Four` (GoF) book. Did I already mentioned that this book is a must read?
</details>

## 57. What are the four Java I/O based classes?
<details>
  <summary>Short Answer</summary>

`Reader`, `Writer`, `InputStream` and `OutputStream`
</details>
<details>
  <summary>Less Short Answer</summary>

These are the four abstract classes that define the basic operations for reading and writing characters and binary data. They have been designed in the mid 90s and you should not use them directly anymore. The preferred patterns that you should use are the factory methods from the `Files.class` these are a `new BufferedReader()` and `new BufferedWriter()` for the reading and writing of characters and `new InputStream()` and `new OutputStream()` for the reading and writing of binary data. These factory methods give you instances built on top of `java.nio`

One last word, you can still decorate the instances you get following the general pattern of the `java.io` API
</details>

## 58. How many objects can you put in a collection?
<details>
  <summary>Short Answer</summary>

It depends on the implementation you have
</details>
<details>
  <summary>Less Short Answer</summary>

`Arraylist` is backed by an array so the limit would be `Integer.MAX_VALUE`, you may be thinking that LinkedList would allow you to store more objects but in fact many things will fail for a LinkedList with more objects than `Integer.MAX_VALUE`. LinkedList counts its element with a field called `size` that is an int and bad things will happen if size reaches `Integer.MAX_VALUE`. The two error method from linked list will not work super well neither since arrays are also indexed by int.

One last word, the same limit also exists from Maps but don't worry there is little chance that you can reach that limit without reaching other limitations in your application
</details>

## 59. What is the maximum length of a String in Java?
<details>
  <summary>Short Answer</summary>

It cannot be longer than `Integer.MAX_VALUE` because it is backed by an array
</details>
<details>
  <summary>Less Short Answer</summary>

First, that would be a very long string indeed and second the number of characters in a string may be different than the length of this array. The reason being there are many characters that are actually encoded on more than one byte.

One last word, the `String.class` changed in 2017 with Java9. The internal array used to be an array of chars 16 bits, it is now an array of bytes 8 bits. This optimization is called `Compact Strings` and can tremendously reduce the memory footprint of your application. One more reason to upgrade to the latest versions of the jdk
</details>

## 60. How does a Set know that it already contains an element?
<details>
  <summary>Short Answer</summary>

It uses the `hashCode()` of the object, if it finds something then it calls the `equals()` method
</details>
<details>
  <summary>Less Short Answer</summary>

A HashSet stalls its objects in the cells of an array. The index of the cell for a given object is computed from the `hashCode()` of this object. This process is very fast because it does not depend on the amount of elements you have in your set. Of course there is a mechanism to handle collisions that is if two different objects happen to have the same hash code.

One last word, because of that HashSet will not work if you override `equals()` for your object without overriding `hashCode()` and one very last word, do not mutate an object once it has been added to a set because you will not be able to find it again
</details>

## 60a. Ad Episode
<details>
  <summary>Answer</summary>

Question number wait I actually did 60 questions that's one hour and one hour is probably longer than most Java coding interviews at least for the technical parts so that's great don't worry there are so many possible questions to be asked that yes there is still plenty of content to cover.

I just would like to take a small break to let you know that I absolutely value your feedback and read all the comments you make so please keep them coming questions, suggestions, anything. Some questions in the comments actually became episodes so that's great thank you for that.

One last word, I created a playlist with all the episodes you can find a link in the descriptions and one very last word, next question 61 will be a real question so stay tuned for more
</details>

## 61. How is `Arrays.asList()` working?
<details>
  <summary>Short Answer</summary>

`Arrays.asList()` wraps an array and exposes it as a list

- It does not copy it
</details>
<details>
  <summary>Less Short Answer</summary>

First, you can `Arrays.asList()` with a vararg but you can also pass an array. Avoid passing an array of primitive types because what you will get is a list with a single element being the array itself. If you modify the array your path then it will modify the list itself because as I said there is no defensive copy of this array. You can modify the elements of this list but you cannot `add` or `remove` elements from it because you know it's actually an array.

One last word, so what you get with the `Arrays.asList()` is not an unmodifiable list because you can still change its elements, if what you need is an unmodifiable list you may consider using `List.of()`
</details>

## 62. Can you cite some methods from the Stream API?
<details>
  <summary>Short Answer</summary>

The three basic methods are `map()`, `filter()` and `reduce()`
</details>
<details>
  <summary>Less Short Answer</summary>

Those are that you will not use reduce match because you have many specialized method to reduce the elements of your stream like `toList()`, `forEach()`, `findFirst()` or `findAny()`. Other intermediate methods you can cite `flatMap()` of course `distinct()`, `sorted()` . Two things you absolutely need to avoid. Avoid using `pick()` unless you need to debug your stream. `pick` is useless in production, second don't do any side effect in any method of the stream API. It will put you in trouble.

One last word, you can also reduce your stream with the collector API, there are a bunch of available characters in the `Collectors` factory class and you can even create your own
</details>

## 63. What is the `var` keyword in Java?
<details>
  <summary>Short Answer</summary>

A keyword you can use in methods to avoid having to specify the type of a local variable
</details>
<details>
  <summary>Less Short Answer</summary>

`var` is for local variables only, you cannot use it for fields for instance. You may use it for `Anonymous Classes and in that case you will have access to the method you add in your Anonymous class that are not defined in the original type. The type of an anonymous class is called the non-denotable type, you can add fields and method to it and access them if you declare your variable with the `var` keyword.

```java
var v = new Object() {
  private int i = 0;
  public int index() {
      return i;
  }
};
System.out.println("i = " + v.index());
```

One last word, you can use your IDE to see the type in further by the compiler and sometimes the result is unexpected
</details>

## 64. How can you create an Unmodifiable List?
<details>
  <summary>Short Answer</summary>

With the factory method `List.of()`
</details>
<details>
  <summary>Less Short Answer</summary>

There are actually several ways to do that but `List.of()` is the preferred one, be careful with the behavior of `Collections.unmodifiableList()` what it gives you is an unmodifiable view of a list but the list you give as an argument is not defensive copied so if you modify it then this modification will be seen through the view, on the other hand you can pass an array to `List.of()` that will be copied so no funny behavior there.

One last word, be careful because `List.of()` does not accept null values. Why would you put null values in a list? You will get an exception at runtime if you pass an array with a null value in it
</details>

## 65. How can you start a thread?
<details>
  <summary>Short Answer</summary>

There is a start method on a `Thread.class`

`Call start(), not run()`
</details>
<details>
  <summary>Less Short Answer</summary>

Two things a thread is either built on a runnable or is a runnable itself, in both cases a common mistake is to call the run method instead of start. `run` will execute your runnable but in the current thread not in a new thread. Second, calling start() is okay for testing, learning and exploring how threads are working. In a production environment, you should not launch your threads by hand. You should use instead the ExecutorService pattern.

One last word, JDK 21 adds new factory methods on the thread class to create both platform threads and virtual threads, but that would be for another time
</details>

## 66. How can you create a file on the disk with Java I/O?
<details>
  <summary>Short Answer</summary>

Use the create file factory method from the `Files.class`

```java
Files.createFile(...)
```
</details>
<details>
  <summary>Less Short Answer</summary>

There is also a create new file on the file class that is the legacy way of creating files. Creating a writer on output stream on a file can also create this file for you, once again the preferred pattern are in the Files factory class, you can check the new BufferWriter or new OutputStream factory methods they both take an open option arguments standard open options include read, write, append, create or create new among others.

One last word, depending on your file system you can also pass a five attributes to a file creation to handle security for instance
</details>

## 67. What is the class named Class?
<details>
  <summary>Short Answer</summary>

The class that models classes
</details>
<details>
  <summary>Less Short Answer</summary>

The jvm creates an instance of this class for each class it loads. The simplest ways to get a reference on the class objects is to call `getClass()` on any object but you can also use the class itself directly like `String.class` or call the `Class.forName("...")` method passing the name of the class as a string. In any case you always get the same reference to a given class there is only one instance of the class Class that models the string class for instance.

```java
Class<?> myClass = String.class;
System.out.println("Name: " + myClass.getName());
```

One last word, the class Class is the entry point of the reflection API which gives you a way to manipulate objects reflectively a technique that is used by many Frameworks
</details>

## 68. How can you find duplicates in a List?
<details>
  <summary>Short Answer</summary>

It really depends on what you need
</details>
<details>
  <summary>Less Short Answer</summary>

You can check if your list has duplicates by putting this list in a set and comparing the size of the set with the size of the list. You could also use a stream calling `distinct()` and count method on it which also builds the set internally. If you need to find the duplicate elements themselves then you need to build an histogram of these elements create a stream on the list and group the elements by themselves counting them with the counting character.

```java
List<T> list = ...;

Map<T, Long> histo = list.stream().collect(Collectors.groupingBy(Function.identity(), Collectors.counting()))
```

One last word, these techniques are all using maps. A set is in fact a map. With maps you can solve this problem in one pass over your data but you consume more memory. As usual there is a trade-off between computing time and memory conception
</details>

## 69. What is a Sealed type?
<details>
  <summary>Short Answer</summary>

A type that knows all of its extensions
</details>
<details>
  <summary>Less Short Answer</summary>

It can be any type interface, class or abstract class. You need to declare it with the `sealed` keyword and then declare the permitted types with the `permits` closer. Now there are constraints on these permitted types; first, they need to be declared in the same package or in the same module. Second they need to be either `final`, `sealed` or declared non-sealed enum and records are actually final types so you cannot create an open hierarchy by accident, the non-sealed declaration is there for that.

One last word, seal types are enforced both at compile time and at runtime
</details>

## 70. How is `List.of()` working?
<details>
  <summary>Short Answer</summary>

It takes an array or a vararg and makes a defensive copy to create an unmodifiable list
</details>
<details>
  <summary>Less Short Answer</summary>

You can use it with a vararg to create a pre-filled list but you can also pass an array, in that case remember that if it is an array of primitive types what you get is a list with one element which is your array probably not what you want. This list implementation does not accept null values sometimes your IDE can warn you about that but in certain cases it cannot and you will get an exception at runtime.

One last word, you can also create sets with `Set.of()` that works in the same way as `List.of()` and modifiable defensive copy and null values not allowed
</details>