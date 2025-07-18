# Cracking the Java Coding Interview

## 1. What is Java?
<details>
  <summary>Short Answer</summary>

A programming language
</details>

<details>
  <summary>Lesser Short Answer</summary>

An object-oriented programming language with some lists of functional programming in it and actually more and more. Object-oriented programming means four things `abstraction`, `encapsulation`, `inheritance` and `polymorphism` that Java supports all that. One restriction though, it does not support multiple linear returns meaning that one class can only extend one other class. And I have a last one for you, Java is a statically typed language meaning that the type of any variable you create or receive is known ad compiled time even if you define the type with vowel the compiler will guess the type of this variable for you
</details>

## 2. What is the Object class in Java?
<details>
  <summary>Short Answer</summary>
  
The super class of every class you can create
</details>

<details>
  <summary>Less Short Answer</summary>

When you create a class you can explicitly extend another class with the `extends` keyword. You can even declare that you extend the object class, this is fine it's dumb because you don't need it but it's legal.
  
Remember a class can only extend one class in Java, multiple linear returns is not allowed. If you do not declare that your class extends anything, which is fine, then the compiler will make your class extend the object class for you so in the end every class in Java extends the Object class
</details>

## 3. Can you cite methods from the Object class?
<details>
  <summary>Short Answer</summary>

`toString()`, `equals()` and `hashCode()`
</details>

<details>
  <summary>Less Short Answer</summary>

There are more. `getClass()` gives you the class of the subject `wait()`, `notify()` and `notifyAll()` these are used in concrete programming and never call these methods unless you really know what you're doing here. `finalize()`, that one you should not override it anymore because it is deprecated and whatever you put in this method is most of the time buggy, most of the time, and the last one is `clone()` same stay away from this method so in a nutshell `toString()`, `equals()` and `hashCode()` these are the most used ones
</details>

## 4. What are the differences between String and array of chars (char[])?
<details>
  <summary>Short Answer</summary>

String is an object with many useful methods, An array only has methods from object and they are not very useful
</details>

<details>
  <summary>Less Short Answer</summary>

String of character is non-modifiable in Java, once you've created one you cannot modify it. The size of an array is fixed, once created you cannot add elements to it, but you can replace one element by another.

- String is a class with useful methods that chat[] has not
- String is non-modifiable

How can you compare string? Just use their `equals()` method, trying to compare an array with its `equals()` method doesn't do what you would expect. You need to use `equals()` from the arrays factory class(`Arrays.equals()`) and the same goes for the `toString()` method, you need to use `toString()` from the same arrays factory class(`Arrays.toString()`) to properly print an array.

One last word, you can create a string a prominent array of chars by calling `new String()` and passing this array as an argument

```java
char[] letters = {'h', 'e', 'l', 'l', 'o'};
String hello = new String(letters);
```

</details>

## 5. How do you sum the elements of an array?
<details>
  <summary>Answer</summary>

Two solutions are, a dumb one & old-fashioned that everyone knows, and a great one

- The first one iterate over the array, add the elements to the sum variable, don't forget to set it to zero at the start and you're done and the result is 10.
```java
int[] ints = {0, 1, 2, 3, 4};
int sum = 0;
for (int element: ints) {
    sum += element;
}
System.out.println("sum = " + sum); // sum = 10
``` 
- The second one, make your stream from your array and just call `sum()`, of course the result is the same and by the way you can also call `min()`, `max()` and `average()` on the stream. Yes this is the one I prefer, it's simpler cleaner and more readable
```java
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

Java Virtual Machine
</details>

<details>
  <summary>Lesser Short Answer</summary>

The piece of software that can run your Java code. The JVM does many things for you besides running your application among many other things. It handles the memory of your application with an element called the `Garbage Collector` or `GC`. It optimizes the code that you're running with another element called the `Just In Time` compiler or `JIT` and it handles the security of your application making sure that no undesired code can sneak in and be executed on your behalf.

One last word, if someone talks to you about HotSpot that's the name of the open sourced jvm developed by defaults at the Open JDK.
</details>

## 7. How can you sort an array?
<details>
  <summary>Short Answer</summary>

There is a method for that called `Arrays.sort(tab)` that's all. Pass your retreat and that's it.
</details>

<details>
  <summary>Less Short Answer</summary>

When you need to sort something, forget about writing a sort algorithm yourself. What about the best sorting algorithm?, that's actually a tough question but you don't need to worry about that because a `Arrays.sort(...)` does the job for you. Now if you really want to shine during an interview, you can cite three algorithms, `QuickSort`, `HeapSort` and `TimSort`. The one used in a `Arrays.sort(...)` is called `Dual Pivot Quicksort`.

One last word, never cite `BubbleSort` unless you want to say that it's a terrible algorithm
</details>

## 8. What is the main characteristic of the String class?
<details>
  <summary>Short Answer</summary>

This class(String) is non-modifiable
</details>

<details>
  <summary>Less Short Answer</summary>

There is no way to modify an instance of the string class that one it has been created so if you call `"string".toUpperCase()`, it does not change a string, it creates a new strings that holds the results. If you really want a string of characters that you can modify then you can use a specific class called `StringBuilder`. It's not a string it actually wraps an array of chars or bytes you can modify the content of this array and you can create a string from it by calling `toString()` on it.

One last word, you use a plus(`+`) to concatenate strings, forget about using the old string builder pattern, it's useless well most of the time
</details>

## 9. What is the difference between equally call(==) and equals()?
<details>
  <summary>Short Answer</summary>

Equally called(==) compare the references and equals() calls a method
</details>

<details>
  <summary>Less Short Answer</summary>

If you compare strings with equal equal(==), you may get the answer false even if the strings have the same value. In a nutshell equal equal(==) is good to compare things that are not objects, int, long and alike.

You should never compare floats or double with equal equal(==) when you need to compare floats or double, what you should be doing is compute the absolute value of their differences and check if it is lesser than a very small value.

```java
float d1, d2;
if(Math.abs(d1 - d2) < 1e-7) {
    // d1 and d2 are equals
}
```

One last thing everything is a reference in Java so most of the time calling equal equal(==)  on object is wrong
</details>

## 10. What is the relationship between equals() and hashCode()
<details>
  <summary>Short Answer</summary>

Java specification says, if two objects are equals then they should have the same `hashCode()`
</details>

<details>
  <summary>Less Short Answer</summary>

It means that when you override `equals()` then you should always override `hashCode()` as well. The Java spec says two objects that are equals must have the same hash code but the contrary is not true, you can have two objects with the same hash code but that are different.

One last thing, always use your IDE to write these methods, first your IDE, do not forget to override both methods and second it will give you a better implementation than the one you will write well most of the time
</details>

## 11. How can you duplicate an array?
<details>
  <summary>Short Answer</summary>

You have two solutions `Arrays.copyOf()` and `System.arrayCopy()`
</details>

<details>
  <summary>Less Short Answer</summary>

You have a clone method on Arrays `array.clone()` internally, it returns an object that is cast to the right type so performance wise it's not ideal. Both `Arrays.copyOf()` and `System.arrayCopy()` need a destination array in which they copy your source array. `Arrays.copyOf()` of can truncate your source array if it's bigger than the destination array or compact it if it's smaller. `System.arrayCopy()` has a richer API. It can copy a portion of your source array in the destination array.

One last word, `Arrays.copyOf()` calls `System.arrayCopy()` internally, so you can use the one you prefer
</details>

## 12. How can you reverse a String?
<details>
  <summary>Short Answer</summary>

Wrap it in a `StringBuilder` and call `reverse()`
</details>

<details>
  <summary>Less Short Answer</summary>

The String.class is non-modifiable, so you cannot change what the string is. All you can do is create another string and that is the reverse of the first one, looping over the letters of your string to reverse it is actually what the reverse method from `StringBuilder` is doing so don't bother re-inventing the wheel, it's there for you to use it. StringBuilder is a modifiable class so the letters are reversed internally.
  
One last word, to get the reversed string, you just need to call `toString()` on your StringBuilder object
</details>

## 13. What is the functional interface?
<details>
  <summary>Short Answer</summary>

An interface with only one abstract method
</details>

<details>
  <summary>Less Short Answer</summary>

Functional interfaces can be implemented with `Lambda Expressions`. Java is a statically typed language so all your variables have a type and all these types are known at compile time. The type of a Lambda is always a functional interface, no exception. A functional interface can contain any number of default all static methods, it can have any method from the object class as abstract methods and only one abstract method that is the one that your Lambda has to implement.

One last word, you can add the `@FunctionalInterface` annotation on your interface, the compiler will then tell you if you got it right or not
</details>

## 14. What is the difference between overriding and overloading?
<details>
  <summary>Short Answer</summary>

`overriding` has to do with inheritance, `overloading` does not
</details>

<details>
  <summary>Less Short Answer</summary>

`Overloading` is the same method with different parameters, `overriding` is the redefinition of a method from a superclass in a subclass. When your code calls a method with different overloads, the compiler decides which method to call so overloading is result at compile time. This is called early binding. Overriding is not, the compiler cannot resolve the call, it is result at runtime this is called late binding.

One last word, you can prevent a method from being overridden by declaring it final with the `final` keyword, you cannot prevent the method from having different overloads
</details>

## 15. What is a Map?
<details>
  <summary>Short Answer</summary>

An object that maps keys to values
</details>

<details>
  <summary>Less Short Answer</summary>

Map is an interface from the `collections` framework, it's canonical implementation is a `HashMap`. You cannot have duplicates among the keys of a map and a given key can map a single value. There is no concept of multi-map in the `collections` framework where a key can be bound to several value, but you can map a key to a list of values. Only use non-modifiable objects for your keys, small strings, a few characters are enough or longs prefer them over integers even for small values.

One last word, the `HashMap` class supports null keys and null values but please don't do that, it will put you in trouble
</details>

## 16. What is an ArrayList?
<details>
  <summary>Short Answer</summary>

An implementation of the List interface backed by an array
</details>

<details>
  <summary>Less Short Answer</summary>

ArrayList is sometimes called the dynamic array because when the internal array of an ArrayList becomes full, it is transparently copied in a larger array. Be careful though because this array can only grow, it never shrinks so when all the ArrayList can become really fat in your application and eat up a lot of memory.

One last thing, ArrayList is your best choice for List implementation, forget about LinkedList. LinkedLists are good for Stacks, we'll talk more on that another time
</details>

## 17. What is Finally? & Explain Finally?
<details>
  <summary>Short Answer</summary>

`Finally` marks a block after a try block that is always executed when the try block exits
</details>

<details>
  <summary>Less Short Answer</summary>

Always means even if there is a return, a continue, a break or an exception that causes the try block to exit. The finally block is the key tool to properly clean up resources that are not `Auto Closable`, your best choice to open an auto closable resource is the try-with-resources statement because it takes care of the closing of this resource for you. Resources that are not Auto-Closable should be released in a finally block that's the case for `ReentrantLock` for instance or for `Semaphores`.

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

One last word, in case of a return in the try block the finally block is evaluated after the return
</details>

## 18. How to make a class Immutable?
<details>
  <summary>Short Answer</summary>

Use `records` if you can
</details>

<details>
  <summary>Less Short Answer</summary>

If you cannot use record, make all the fields of this class `final` and don't forget to make this class `final` also because if you don't someone could add some mutable state to this class using inner returns and pass it around using polymorphism. Do not forget to make defensive copies of the modifiable objects you get as arguments in your constructor like Lists, Maps and the alike and the same for your accessors make sure they do not leak references to your internal state that could be modifiable, use a defensive copy where you need it.

One last thing, String, Integer, Long and all the wrapper classes of the jdk are non-modifiable, you can check them to see how they work
</details>

## 19. What is the difference between String and StringBuffer and StringBuilder?
<details>
  <summary>Short Answer</summary>

`String` is non-modifiable, `StringBuilder` is modifiable and `StringBuffer` is thread safe
</details>

<details>
  <summary>Less Short Answer</summary>

`StringBuffer` is rarely used. `StringBuilder` is nice for certain string manipulations like reversing(`reverse()`) a string or inserting(`insert()`) a character. Should you use StringBuilder to concatenate strings? Most of the time no, if you're using Java 9 and later, string concatenation with plus(+) has been optimized. If you're using Java 8, then in many cases concatenation with plus is in fact compiled with `StringBuilder`

One last word, if you are joining string elements from a List or an Array consider using `String.join()` the `StringJoiner` class and the `Collectors.joining()` collector.
</details>

## 20. How to make a Singleton?
<details>
  <summary>Short Answer</summary>

One pattern, you use an `enum` with a single value
</details>

<details>
  <summary>Less Short Answer</summary>

The pattern that uses a class with a private constructor, a private static field and a factory method that tests if the private field is new or not is more complex either non-thread safe or buggy or both. Making it thread safe using a double check locking is also buggy, just look for this bug on your favorite search engine. Using an enum is super simple, thread safe, guaranteed bug free at the jvm level and recommended by the best experts.

One last word, this any based pattern is used in many places in the jdk, you can check the source code of the `Comparator.naturalOrder()` factory method for example
</details>

## 21. What is a static method?
<details>
  <summary>Short Answer</summary>

A method declared with the `static` keyword
</details>

<details>
  <summary>Less Short Answer</summary>

A method that you can invoke without creating any object. You can invoke a static method with a class name, you can even invoke a static method through a null object. A static method cannot call a `non-static` method from the same class. Static methods are useful to implement processors or computations, some classes only have static methods like Math, Arrays or Collections.

```java
class Scratch {
    public static void main(String[] args) {
        Scratch scratch = null;
        scratch.print();
    }
    private static void print() {
        System.out.println("print...");
    }
}
```

One last word, static methods are sometimes called Factory methods because they can be used to create objects in a certain way like `List.of()` that creates an empty list. Classes with only static methods are sometimes called Factory classes.
</details>

## 22. How can you find a character in a String?
<details>
  <summary>Short Answer</summary>

There is a method for that called `indexOf()`
</details>

<details>
  <summary>Less Short Answer</summary>

The `string.indexOf()` method has several overloads, one just take a character in the form of an int, another char and int because Java supports Unicode and some characters cannot be encoded on a single char, another one takes a string because `indexOf()` can also find small strings in bigger strings. Both can also take an index used to start the search from, indexOf returns the index or the first occurrence of the character or the string so if you want to find all the occurrences of a single letter you can loop in that way.

```java
public static void main(String[] args) {
    String s = "abcabcabd";
    int index = s.indexOf('b');
    System.out.println("index: " + index);
    while (index > 0) {
        index = s.indexOf('b', index + 1);
    }
    System.out.println("index: " + index);
}
```

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
```java
DoubleUnaryOperator op = d -> Math.sqrt(d);
DoubleUnaryOperator op = d -> Math::sqrt;
```
- `bound method references`, the classical `System.out::println` is a bound method reference
```java
Consumer<String> c = s -> System.out.println(s);
Consumer<String> c = System.out::println;
```
- `unbound method references`, are they may look like static calls like this one, but they are not so be careful
```java
ToIntFunction<String> f = s -> s.length();
ToIntFunction<String> f = String::length;
```
- `constructor method references` like this one
```java
Supplier<List<String>> sup = () -> new ArrayList<>();
Supplier<List<String>> sup = () -> ArrayList::new;
```

One last word, to translate a method reference to Lambda, you need to know its exact type. One very last word, method references are there to improve the readability of your code so if you feel your code is actually less readable with them don't use them
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

What you have in a class file is the byte code of your class, this bytecode is first interpreted by your Java Virtual Machine. Running your Java code in that way is super slow so a first JIT compiler called `C1` compiled it to machine language. The C1 compiler does a nice job but your compiled code can be optimized even further. That's the job of a second JIT compiler `C2`. C2 carefully analyzes the way your code is running and compiles it again to leverage some more optimization.

One last word, if at some point C2 sees that it can do better, it will de-optimize your code and optimize it again
</details>

## 26. What kind of method can you override?
<details>
  <summary>Short Answer</summary>

Instance methods
</details>
<details>
  <summary>Less Short Answer</summary>

`static` methods cannot be overridden because you call them using an explicit class name so even if a Class B extends a Class A and defines the same static method you can still call each of them. Instance method can be overridden as long as they are non-private, non-final and that their class can be extended. The obvious way to prevent a class from being extended is to make it `final`, but you can also declare it's NoArgConstructor private.

```java
class Scratch {
    public static void main(String[] args) {
        System.out.println("A: " + A.name());
        System.out.println("B: " + B.name());
        // A: A
        // B: B
    }
}
class A {
    public static String name() {
        return "A";
    }
}
class B extends A {
    public static String name() {
        return "B";
    }
}
```

- Safe way: copy the method declaration

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

```java
class Scratch {
    public void print(String name) {
        System.out.println("print:" + name);
    }
    
    // Compiled Error: 'print(String)' is already defined in 'Scratch'
    public String print(String name) throws Exception {
        System.out.println("print:" + name);
        return name;
    }
}
```

One last word, this rule holds even if one of this method is abstract because it would force the implementation to break this rule

```java
abstract class AbstractScratch {
    public abstract void print(String name);

    // Compiled Error: 'print(String)' is already defined in 'AbstractScratch'
    public abstract String print(String name) throws Exception;
}

```
</details>

## 28. What is a marker interface?
<details>
  <summary>Short Answer</summary>

An interface with no method that is just here to Mark a class
</details>
<details>
  <summary>Less Short Answer</summary>

Being a marker interface is not really a language or an API notion, it's just a way of describing the nature of some interfaces. There are several examples in the JDK of such interfaces `serializable` of course that allows the instance of a class to be serialized and the `cloneable` that allows instances of a class to be cloned.

One last thing, because there is no method in these interfaces, you need to check if the object you have is an instance of this interface. It can be done with `instanceOf()` or directly at the class level with the method is assignable from defined on the class of Class (`Class.isAssignableFrom()`)
</details>

## 29. What is the difference between Collection and Set?
<details>
  <summary>Short Answer</summary>

There are no duplicate elements in the Set
</details>
<details>
  <summary>Less Short Answer</summary>

`Collection` and `Set` are interfaces from the collections framework. `Set` extends Collection all the instance method defined in the Set interface override method from collection and are re-defined to modify the semantic. They do not work in the same way. The set interface is implemented by `HashSet` which has another very interesting property, its implementation of the `contains()` method is super fast, much faster than the one from ArrayList.

One last word, if you need both the iterability property of ArrayList and the fast container implementation, you may take a look at the `LinkedHashSet` class which unfortunately is not a List.
</details>

## 30. How does finalize() work?
<details>
  <summary>Short Answer</summary>

It does not work
</details>
<details>
  <summary>Less Short Answer</summary>

`finalize()` has been deprecated in Java 9 and deprecated for removal in Java 18, so stop using it. `finalize()` is supposed to be a method called by some undefined elements when the garbage collector detects that an object is not reachable anymore.

Here are two of the major issues with finalizer; First, the thread running finalized is not specified those are that you can get race conditions in this method. Second, it may take a lot of time for this method to be called, the correctness of your code should never rely on the fact that finalize is called.

One last word, there is a replacement pattern called `The Cleaner Pattern`, you can check the cleaner class for more information
</details>

## 31. What are the main features of java 8?
<details>
  <summary>Short Answer</summary>

Lambda Expressions
</details>
<details>
  <summary>Less Short Answer</summary>

This version so Lambda expression added to the language but there are many other things that have been added to Java 8. The collections frameworks has been rewritten with many new features and methods. The stream API is a very clean implementation of `map`, `filter`, `reduce` that you can use in parallel. The completable future API is an asynchronous programming model added to the JDK and many many small things here and there to make your developer life better. 

One last word, Java 8 was released in March 2014 as of this recording that was 9 years ago if you're still working on this version, you should really consider moving to a more recent one
</details>

## 32. Do streams and collections have common methods?
<details>
  <summary>Short Answer</summary>

Yes and no, they do have one method that is called the same and take the same parameter
</details>
<details>
  <summary>Less Short Answer</summary>

This method is called `foreach()`, it takes a consumer and you have it on both the `stream` interface and the `iterable` interface that being said even if they are basically doing the same thing, these methods are not implemented in the same way. Most of the time you can call directly `collections.foreach(...)` instead of calling `collections.stream().foreach()` that makes you save the creation of the stream object if you don't use it why would you want to create it.

```java
List<String> letters = List.of("h", "e", "l", "l", "o");
letters.forEach(System.out::println);

letters.stream().forEach(System.out::println);
```

One last word, even if collections and streams are there to process data there are many differences between them but that's for another time
</details>

## 33. How can you tell that a string is an anagram of another string?
<details>
  <summary>Short Answer</summary>

The easy way, sort the letters of the strings and just compare them
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

One last word, be careful not to overflow when you're doing the multiplication, it can happen for long strings of characters
</details>

## 34. On what kind of source can you build a Stream?
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

The pattern is `stream().collect(...)` and pass `Collectors.groupingBy(...)` and then you need to pass a function to this groupingBy(). This function maps each element of your stream to a key that is then added to your map. The corresponding element is itself added to a list bound to this key so if several elements of your streams are mapped to the same key you will find them together in this list.

```java
cities().stream().collect(Collectors.groupingBy(City::state))
// -> Map<State, List<City>>
```

One last word, you can post process this list with another collector, pass as a second argument to this groupingBy(), this other collector is called the Downstream Collector.
</details>

## 36. What is the difference between FIFO and LIFO?
<details>
  <summary>Short Answer</summary>

`FIFO` is a queue, `LIFO` is a stack
</details>
<details>
  <summary>Less Short Answer</summary>

`FIFO` stands for `F`irst `I`n `F`irst `O`ut and `LIFO` stands for `L`ast `I`n `F`irst `O`ut.

There are two interfaces in the jdk to model these, queue, that models the FIFO that is extended by `deque` and that's the second interface that models for LIFO. The preferred implementation for both of these interfaces is `ArrayDeque` but it's not thread safe. If you need a thread safe implementation you can use a `ConcurrentLinkedQueue` for queue or `ConcurrentLinkedDeque` for deque.

One last word, there is a Stack class in a jdk that is an extension of the Vector class. Both `Stack` and `Vector` have been deprecated a long time ago, so you should not use them anymore
</details>

## 37. What is the GOF?
<details>
  <summary>Short Answer</summary>

The nickname of the fundamental book on design patterns
</details>
<details>
  <summary>Less Short Answer</summary>

The full title of this book is `Design patterns; Elements Of Reusable Object-Oriented Software`. It was published in 1994. The four authors are `Erich Gamma`, `Richard Helm`, `Ralph Johnson` and `John Vlissides`. This book contains a 23 design patterns in three categories; 

- Creational: with the Builder, the Factory, the Singleton
- Structural; with the Adapter, the Decorator, the Proxy
- Behavioral; with the Iterator the Strategy, the Visitor.

One last word, this book is a must-read. The examples are written in C++ but it's easy enough to convert them to Java or to your favorite language
</details>

## 38. How can you create a Comparator?
<details>
  <summary>Short Answer</summary>

Just use the factory methods of the `Comparator` interface
</details>
<details>
  <summary>Less Short Answer</summary>

This interface has a bunch of factory methods to create comparators that compare objects using one of their fields, it also has default methods to modify the behavior of a given comparator. For instance, you can compare people using their last name and in case you have people with the same last name you can then compare them using their first name. In case you want to use this comparator to sort a list of people but need to sort them in the reverse order and then you can call reversed() on an existing comparator.

```java
var userComparator = Comparator
        .comparing(User::lastName)
        .thenComparing(User::firstName)
        .reversed();
```

One last thing, null values are always painful to handle when you want to sort a list. The comparator interface has also a `nullsFirst()` and `nullsLast()`.

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

They are actually more, the definition of a functional interface is such that some existing interfacers became functional with Java 8. Because you can implement a functional interface with a Lambda, it means that if you have old interfaces in your application that qualify for functional interfaces and then you can use lambdas to implement them without having to recompile them. That's why the `@FunctionalInterface` annotation is not mandatory on the functional interface.

One last word, you want more sure `Executor` even `Comparable` is a functional interface though I'm not sure that you want to implement this one with another expression
</details>

## 40. How can you open a file for writing some text?
<details>
  <summary>Short Answer</summary>

There is a factory method for that in the `Files` class
</details>
<details>
  <summary>Less Short Answer</summary>

There are actually two patterns; one from the old days of `java.io` and the less old one from `java.nio` and this is the one you should prefer. The exact pattern is the `Files.newBufferedWriter(...)` that takes a path as an argument, it has several overloads.

```java
var writer = Files.newBufferedWriter(
        path,
        StandardCharsets.ISO_8859_1,
        StandardOpenOption.CREATE,
        StandardOpenOption.APPEND
);
```

You can specify the Charsets used by your text file, the default value being utf-8 and you can specify some open options. Do you want to create the file if it does not exist and if it does do you want to erase its content or append to it?

One last word, what you get is still a buffered writer that you can still decorate if you need
</details>

## 41. What is the difference between a Sorted and an Ordered Collection?
<details>
  <summary>Short Answer</summary>

Sorted means that you can compare your elements, Ordered means that you can access them using an index
</details>
<details>
  <summary>Less Short Answer</summary>

It has to do with how you can iterate over the elements of your collection. The sorted collection gives you the smallest element first up to the largest one. If you add an element to a sorted collection, you may change the iteration order. An ordered collection on the other hand respects the order in which you add your elements so the first element is the first that has been added up to the last one.

One last word, ordered collections are modeled by the Lists in the collection framework, your favorite implementation is a `ArrayList` and sorted collections are modeled by NavigableSet implemented by `TreeSet`
</details>

## 42. How can you open a file for reading binary data?
<details>
  <summary>Short Answer</summary>

There is a factory method for that on the `Files` class
</details>
<details>
  <summary>Less Short Answer</summary>

The all patterns from Java 1.1 based on the decoration pattern are still there, but you should use the Files factory class to create your readers, writers, input stream and output stream.

```java
Files.newInputStream(path);
```

The implementations you will get are built on top of `java.nio` and they are going to give you better performances. You can still use The Decorator pattern if you need to build data input stream or data output streamed, gzip streams or streams that mixed text and data. 

One last word, using the patterns from the Files factory class also give you final control on the opening of files on the `CharSet` you can use to read your text files and they are built to use the path object instead of file objects which is better
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

An Array is an object but with a default `toString()` method that you cannot override so printing it on the console directly gives you something that you do not want. You can call `Arrays.toString()` and pass your array it will print the content of your array on called toString() on each element of this array if it is an object. If you are not happy with the formatting you then need to iterate on the elements of this array or create a stream on it and create the strings of characters you need.

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

It is a Set that keeps its elements sorted
</details>
<details>
  <summary>Less Short Answer</summary>

First point, it's a Set so it does not have any duplicates if you add two elements that are equal then the second one will not be added. Second point the elements you add must be Comparable or if they are not you must provide a comparator when you create your SortedSet. If you provide a comparator, it will be used even if your elements are comparable and when you iterate over them they will be sorted in the increasing order. As of Java 6, you should favor `NavigableSet` instead of SortedSet that gives you more method than total Sets.

One last word, the default implementation is `TreeSet` which implements a Red Black Tree
</details>

## 45. What pattern has been used to create the Java I/O API?
<details>
  <summary>Short Answer</summary>

The Decorator Pattern
</details>
<details>
  <summary>Less Short Answer</summary>

The Decorator Pattern is a `Structural Pattern` from the `Gang of Four` (GoF) book. A decorator is in fact a wrapper on an object that extends the class of that object, it may add more methods or change the way the existing methods are working. Wrapping an existing object means that it's constructor takes an object of the superclass as a parameter so it is both `an extension` and `a composition` for instance `BufferedReader` extends Reader and adds readline() method, plus the reading works with a buffer.

One last word, you should use the `Files` factory class to build the base objects, you need to read and write content to files, but you can still decorate them to add features to the base objects you get
</details>

## 46. What are the different categories of design patterns?
<details>
  <summary>Short Answer</summary>

3 categories; `Creational`, `Structural`, `Behavioral`
</details>
<details>
  <summary>Less Short Answer</summary>

It refers to the `Gang of Four` (GoF) book a must-read for every developer. Some creational patterns; `Factory`, `Builder` and `Singleton`, some structural patterns; `Decorator`, `Facade`, `Proxy`, some behavioral patterns; `Iterator`, `Template Method` and a well-known `Visitor`. The GoF gives you C++ implementations, some of them are updated but the ideas are still excellent.

One last word, there are many patterns that are so widely used that you use them even if you don't know them. That's the case for the Iterator Pattern or the Factory Pattern
</details>

## 47. How can you count how many times a letter appears in a String?
<details>
  <summary>Short Answer</summary>

You need to iterate over the string in one way or another
</details>
<details>
  <summary>Less Short Answer</summary>

Two ways; first, you can look for your letter in a string with `indexOf()` until you don't find it anymore. `indexOf()` may take an index where it will start its search that's a quick and efficient pattern. Second pattern, you can stream on the letters of the stream removing the letters that do not match and count the result, efficient, more functional, more readable, this is the one I prefer.

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

One last word, the `count()` method return the long that you can safely cast to an end. A string of character is backed by an Array so there is no way you can have more than `Integer.MAX_VALUE` letters
</details>

## 48. What is a bucket in a Map?
<details>
  <summary>Short Answer</summary>

A cell in an array
</details>
<details>
  <summary>Less Short Answer</summary>

The HashMap class from the collections framework is backed by an `Array`, when you add a key to a HashMap a special hash code is evaluated for that key to choose which cell of the array will receive the key value pair. If there is already a different key value pair in this cell, this is called the `collision` and then a `LinkedList` is created to add this second pair and if there are too many, this LinkedList is actually replaced by your `Red Black Tree` to minimize collisions when the amount of key value pairs reaches `75%` of the size of the array then it is copied in a new larger array.

One last word, this copying incurs the re-hashing of all the keys present in a map which may be costly so be careful about that and try to create maps with the right size
</details>

## 49. What does Synchronized mean?
<details>
  <summary>Short Answer</summary>

It is a keyword that prevents more than one thread to execute a given block of code at the same time
</details>
<details>
  <summary>Less Short Answer</summary>

Synchronization has to do with concurrent programming, this block of code can be a delimited block inside the method or it can be the wall method static or not. All synchronized blocks need an object that they use as a key, you can use the same key for more than one synchronized block. In the case of a synchronized method then the key is the object itself or the class if the method is static. There are limitations with synchronized block that you don't have with `ReentrantLock` so we can use these objects instead.

One last word, never expose your key or your locks. It will help you prevent `Deadlocks` a situation that you absolutely want to avoid
</details>

## 50. What is the difference between a Collection and a Stream?
<details>
  <summary>Short Answer</summary>

A collection contains an object, a stream is empty
</details>
<details>
  <summary>Less Short Answer</summary>

A collection is meant to carry objects around with methods to handle them, most of the time your stream is an empty object that you can connect to a source of objects to process them. This source can be a collection, an array and many other things. You can even connect a stream to your own source of data if you need it. It will then process your elements one by one lazily. Some methods like `findAny()` or `allMatch()` can interrupt the processing of these objects.

One last word, there are actually two methods that need to remember the processed object; `distinct()` and `sorted()` so if you're using them then your stream will not be empty anymore
</details>

## 51. What is the difference between a File and a Path?
<details>
  <summary>Short Answer</summary>

A File is a class and the Path is an interface
</details>
<details>
  <summary>Less Short Answer</summary>

The File class is from Java 1.0 but is from `java.nio` released with Java 7. An instance of file is the same no matter what file system you're using because Path is an interface, the instance you build depends on the file system. You can get attributes that are specific to these file systems like security attributes. As of now, you should favor the use of path objects over file objects.

One last word, creating an instance of file all path does not create the corresponding file or directory on your disk, you need to call `createNewFile()` on the File class or the `Files.createFile()` Factory method that takes a path as an argument to do that
</details>

## 52. What is the difference between a Checked and an Unchecked Exception?
<details>
  <summary>Short Answer</summary>

You need to write special code to handle the checked exception, not for unchecked exceptions
</details>
<details>
  <summary>Less Short Answer</summary>

All your exceptions extend the `Exception.class` if an exception actually extends `Runtime` exception then it is an unchecked exception if it does not then it is checked exceptions. You need to handle your checked exceptions either by catching them or by declaring them in the `throws` clause of your methods and constructors. You do not need to do that for unchecked exceptions.

One last word, all these classes extend themselves the `Throwable.class` also extended by the `Error.class`. Errors are also unchecked exceptions but reserved for serious problems like Out Of Memory `OOM` error or Stack Overflow error
</details>

## 53. What is a Stream?
<details>
  <summary>Short Answer</summary>

An object that implements the `map`, `filter`, `reduce` pattern
</details>
<details>
  <summary>Less Short Answer</summary>

The stream consumes elements from a source and can do several operations, these operations are organized in a pipeline where each element is passed from one step of the pipeline to the next one. Mapping an element consists in transforming it, filtering consists in deciding if this element should be transmitted or not based on a predicate and reducing may consist in many things; summing the elements, extracting a min or a max or adding them to a list or a map.

One last word, the stream API allows you to conduct these computations in parallel, still you need to be careful with that as always when it comes to optimizations measure, don't guess
</details>

## 54. What is the hash code of an object?
<details>
  <summary>Short Answer</summary>

A mapping of an object to an integer
</details>
<details>
  <summary>Less Short Answer</summary>

The idea behind the hash code is to represent any object within it so that you can quickly tell if two objects are different by just comparing their hash code. Indeed, the specification says that two objects that are equal must have the same hash code but it turns out that two different objects may also have the same hash code so if two objects have different hash code then they cannot be equal but if they have the same hash code then you need to compare them to see if they are equal.

One last word, there are many ways of computing hash codes some are better than others, if you're not sure on what you need relying on your IDE to generate the hash code method is probably your safest choice.
</details>

## 55. What is an ExecutorService?
<details>
  <summary>Short Answer</summary>

An object to which you can submit tasks to be executed in another thread
</details>
<details>
  <summary>Less Short Answer</summary>

ExecutorService is an interface part of the `java.util.concurrent` API added to the `JDK 5` in 2004. It's the preferred way to run tasks in another thread. In fact, you shouldn't be creating threads by calling `new Thread()` anymore. A task can be either a `Runnable` or `Callable` that you can implement with a lambda expression, submitting a task gives you a Future object that you can use to get a result and exception if something goes wrong. All that you can use to interrupt the running of this task.

One last word, an ExecutorService is sometimes called the `Pool of Threads` and most of the time it is but it can also create threads on demand which is what it is doing for Virtual Threads for instance.
</details>

## 56. What is an Iterator?
<details>
  <summary>Short Answer</summary>

An object used to iterate over the elements of a Collection
</details>
<details>
  <summary>Less Short Answer</summary>

Iterator is an interface with three method; `hasNext()` that tells you if there are more objects to iterate over we should call this method first then if it returns true, you can call `next()` to get the next object and move the iterator one step. It also has a `remove()` method that can throw an `UnsupportedOperationException` you need that if your collection is immutable. Most of the time you use iterators for collections but iterators can actually be created without them. For instance, you can create a `RangeIterator` that can iterate over a range of integers.

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

One last word, the iterator pattern is actually a pattern from the `Gang of Four` (GoF) book. Did I already mention that this book is a must-read?
</details>

## 57. What are the 4 Java I/O based classes?
<details>
  <summary>Short Answer</summary>

`Reader`, `Writer`, `InputStream` and `OutputStream`
</details>
<details>
  <summary>Less Short Answer</summary>

These are the 4 abstract classes that define the basic operations for reading and writing characters and binary data. They have been designed in the mid 90s and you should not use them directly anymore. The preferred patterns that you should use are the factory methods from the `Files.class`, these are a `new BufferedReader()` and `new BufferedWriter()` for the reading and writing of characters and `new InputStream()` and `new OutputStream()` for the reading and writing of binary data. These factory methods give you instances built on top of `java.nio`

One last word, you can still decorate the instances you get following the general pattern of the `java.io` API
</details>

## 58. How many objects can you put in a collection?
<details>
  <summary>Short Answer</summary>

It depends on the implementation you have
</details>
<details>
  <summary>Less Short Answer</summary>

`Arraylist` is backed by an Array so the limit would be `Integer.MAX_VALUE`, you may be thinking that LinkedList would allow you to store more objects but in fact many things will fail for a LinkedList with more objects than `Integer.MAX_VALUE`. LinkedList counts its element with a field called `size` that is an int and bad things will happen if size reaches `Integer.MAX_VALUE`. The `toArray()` method from LinkedList will not work super well neither since Arrays are also indexed by int.

One last word, the same limit also exists from `Maps` but don't worry there is little chance that you can reach that limit without reaching other limitations in your application.
</details>

## 59. What is the maximum length of a String in Java?
<details>
  <summary>Short Answer</summary>

It cannot be longer than `Integer.MAX_VALUE` because it is backed by an Array
</details>
<details>
  <summary>Less Short Answer</summary>

First, that would be a very long string indeed and second the number of characters in a string may be different than the length of this array. The reason being there are many characters that are actually encoded on more than one byte.

One last word, the `String.class` changed in 2017 with Java9. The internal array used to be an array of chars 16 bits, it is now an array of bytes 8 bits. This optimization is called `Compact Strings` and can tremendously reduce the memory footprint of your application. One more reason to upgrade to the latest versions of the JDK.
</details>

## 60. How does a Set know that it already contains an element?
<details>
  <summary>Short Answer</summary>

It uses the `hashCode()` of the object, if it finds something then it calls the `equals()` method
</details>
<details>
  <summary>Less Short Answer</summary>

A HashSet stalls its objects in the cells of an Array. The index of the cell for a given object is computed from the `hashCode()` of this object. This process is very fast because it does not depend on the amount of elements you have in your Set. Of course there is a mechanism to handle collisions that is if two different objects happen to have the same hash code.

One last word, because of that HashSet will not work if you override `equals()` for your object without overriding `hashCode()` and one very last word, do not mutate an object once it has been added to a set because you will not be able to find it again

```java
import java.util.HashSet;
import java.util.Objects;
import java.util.Set;

class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Person person = (Person) obj;
        return age == person.age && Objects.equals(name, person.name);
    }

    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}
class Scratch {
    public static void main(String[] args) {
        Set<Person> set = new HashSet<>();

        Person person = new Person("John", 30);
        set.add(person);

        System.out.println("Set contains: " + set.contains(person)); // true

        // Mutate the object after adding it to the Set
        person.setName("Jane");
        person.setAge(25);

        // Try to find the object in the Set again
        System.out.println("Set contains: " + set.contains(person)); // false

        // The object is still in the Set, but we can't find it because its hash code has changed
        System.out.println("Set elements: " + set);
    }
}
/*
Set contains: true
Set contains: false
Set elements: [Jane (25)]
 */
```
</details>

## 60a. Ad Episode
<details>
  <summary>Answer</summary>

Question number wait I actually did 60 questions that's one hour and one hour is probably longer than most Java coding interviews at least for the technical parts so that's great. Don't worry, there are so many possible questions to be asked that yes there is still plenty of content to cover.

I just would like to take a small break to let you know that I absolutely value your feedback and read all the comments you make so please keep them coming questions, suggestions, anything. Some questions in the comments actually became episodes so that's great thank you for that.

One last word, I created a playlist with all the episodes you can find a link in the descriptions and one very last word, next question 61 will be a real question so stay tuned for more
</details>

## 61. How is `Arrays.asList()` working?
<details>
  <summary>Short Answer</summary>

`Arrays.asList()` wraps an array and exposes it as a List

- It does not copy it
</details>
<details>
  <summary>Less Short Answer</summary>

First, you can call `Arrays.asList()` with a vararg but you can also pass an Array. Avoid passing an array of primitive types because what you will get is a list with a single element being the array itself. If you modify the array you pass then it will modify the list itself because as I said there is no defensive copy of this array. You can modify the elements of this list but you cannot `add` or `remove` elements from it because you know it's actually an Array.

One last word, so what you get with the `Arrays.asList()` is not an Unmodifiable List because you can still change its elements, if what you need is an Unmodifiable List you may consider using `List.of()`
</details>

## 62. Can you cite some methods from the Stream API?
<details>
  <summary>Short Answer</summary>

The 3 basic methods are `map()`, `filter()` and `reduce()`
</details>
<details>
  <summary>Less Short Answer</summary>

Those are that you will not use reduce match because you have many specialized method to reduce the elements of your stream like `toList()`, `forEach()`, `findFirst()` or `findAny()`. Other intermediate methods you can cite `flatMap()` of course `distinct()`, `sorted()` . 2 things you absolutely need to avoid. Avoid using `pick()` unless you need to debug your stream. `pick()` is useless in production, second don't do any side effect in any method of the stream API. It will put you in trouble.

One last word, you can also reduce your stream with the collector API, there are a bunch of available characters in the `Collectors` factory class and you can even create your own.
</details>

## 63. What is the `var` keyword in Java?
<details>
  <summary>Short Answer</summary>

A keyword you can use in methods to avoid having to specify the type of a local variable
</details>
<details>
  <summary>Less Short Answer</summary>

`var` is for local variables only, you cannot use it for fields for instance. You may use it for `Anonymous Classes` and in that case you will have access to the method you add in your Anonymous class that are not defined in the original type. The type of an Anonymous class is called the Non-Denotable type, you can add fields and method to it and access them if you declare your variable with the `var` keyword.

```java
var v = new Object() {
  private int i = 0;
  public int index() {
      return i;
  }
};
println("i = " + v.index());
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

There is a `start()` method on a `Thread.class`

`Call start(), not run()`
</details>
<details>
  <summary>Less Short Answer</summary>

Two things a thread is either built on a Runnable or is a Runnable itself, in both cases a common mistake is to call the run method instead of start. `run()` will execute your Runnable but in the current thread not in a new thread. Second, calling `start()` is okay for testing, learning and exploring how threads are working. In a production environment, you should not launch your threads by hand. You should use instead the `ExecutorService` Pattern.

One last word, JDK 21 adds new factory methods on the Thread class to create both `Platform` threads and `Virtual` threads, but that would be for another time
</details>

## 66. How can you create a file on the disk with Java I/O?
<details>
  <summary>Short Answer</summary>

Use the `createFile()` factory method from the `Files.class`

```java
Files.createFile(...)
```
</details>
<details>
  <summary>Less Short Answer</summary>

There is also a `createNewFile()` on the File class that is the legacy way of creating files. Creating a writer on output stream on a File can also create this file for you, once again the preferred pattern are in the Files factory class, you can check the `new BufferWriter()` or `new OutputStream()` factory methods they both take an open option arguments standard open options include read(), write(), append(), create() or createNew() among others.

One last word, depending on your file system, you can also pass 5 attributes to a file creation to handle security for instance
</details>

## 67. What is the class named Class?
<details>
  <summary>Short Answer</summary>

The class that models classes
</details>
<details>
  <summary>Less Short Answer</summary>

The JVM creates an instance of this class for each class it loads. The simplest ways to get a reference on the class objects is to call `getClass()` on any object but you can also use the class itself directly like `String.class` or call the `Class.forName("...")` method passing the name of the class as a string. In any case you always get the same reference to a given class there is only one instance of the Class.class that models the String class for instance.

```java
var c1 = "hello".getClass();
var c2 = String.class;
var c3 = Class.forName("java.lang.String");
```

One last word, the Class class is the entry point of the reflection API which gives you a way to manipulate objects reflectively, a technique that is used by many frameworks
</details>

## 68. How can you find duplicates in a List?
<details>
  <summary>Short Answer</summary>

It really depends on what you need
</details>
<details>
  <summary>Less Short Answer</summary>

You can check if your list has duplicates by putting this List in a Set and comparing the size of the set with the size of the list. You could also use a stream calling `distinct()` and count()` method on it which also builds the Set internally. If you need to find the duplicate elements themselves then you need to build an histogram of these elements, create a stream on the list and group the elements by themselves counting them with the counting character.

```java
List<T> list = ...;

Map<T, Long> histo = list.stream().collect(Collectors.groupingBy(Function.identity(), Collectors.counting()))
```

One last word, these techniques are all using Maps, a Set is in fact a map. With maps you can solve this problem in one pass over your data but you consume more memory. As usual there is a trade-off between computing time and memory conception.
</details>

## 69. What is a Sealed type?
<details>
  <summary>Short Answer</summary>

A type that knows all of its extensions
</details>
<details>
  <summary>Less Short Answer</summary>

It can be any type interface, class or abstract class. You need to declare it with the `sealed` keyword and then declare the permitted types with the `permits` closer. Now there are constraints on these permitted types; first, they need to be declared in the same package or in the same module. Second they need to be either `final`, `sealed` or declared `non-sealed enum and records are actually final types so you cannot create an open hierarchy by accident, the non-sealed declaration is there for that.

```java
sealed interface Shape permits Circle, Square, RandomShape {}
final class Circle implements Shape {}
record Square implements Shape {}
non-sealed class RandomShape implements Shape {}
```

One last word, seal types are enforced both at `compile time` and at `runtime`
</details>

## 70. How is `List.of()` working?
<details>
  <summary>Short Answer</summary>

It takes an Array or a vararg and makes a defensive copy to create an Unmodifiable List.
</details>
<details>
  <summary>Less Short Answer</summary>

You can use it with a vararg to create a pre-filled list but you can also pass an array, in that case remember that if it is an array of primitive types what you get is a list with one element which is your array probably not what you want. This List implementation does not accept null values, sometimes your IDE can warn you about that but in certain cases it cannot and you will get an exception at runtime.

```java
public static void main(String[] args) {
    int[] intArray = {1, 2, 3};
    List<int[]> intsList = List.of(intArray);
    System.out.println(intsList.size()); // > 1
}
// or
public static void main(String[] args) {
    Integer[] intArray = {1, 2, 3};
    List<Integer> intsList = List.of(intArray);
    System.out.println(intsList.size()); // > 3
}
```

One last word, you can also create sets with `Set.of()` that works in the same way as `List.of()` and modifiable defensive copy and null values not allowed.
</details>

## 71. What is the difference between Runnable and Thread?
<details>
  <summary>Short Answer</summary>

`Runnable` is an interface and `Thread` is a class
</details>
<details>
  <summary>Less Short Answer</summary>

The Runnable is a model for a task you can implement it with Lambda that does not take anything and returns nothing. You can execute this lambda by calling its `run()` method. You can then create a thread object passing your runnable as an argument and then execute this runnable in this thread by calling the `start()` method of that thread object. Be careful not to use the `thread.run()` method, it will execute your runnable but in the current thread.

```java
Runnable task = () -> System.out.println(Thread.currentThread().getName());

// or
Thread t = new Thread(task);
t.start();
t.run() // NO !!

// or
ExecutorService service = ...;
service.submit(task);
```

One last word, this pattern is okay for playing with threads and understanding how they work. In a real application, you should use the `ExecutorService` pattern instead of this one
</details>

## 72. What is the difference between `map()` and `flatMap()`?
<details>
  <summary>Short Answer</summary>

These are 2 methods from the stream API to map objects of a given type to objects of another type
</details>
<details>
  <summary>Less Short Answer</summary>

`map()` is super simple, it takes a function like `String::length` that maps strings of characters to their name.

```java
var lengthOfStrings = Stream.of("one", "two", "three")
        .map(String::length)
        .toList();
```
`flatMap()` works differently, it maps one-to-many relationships. The mapping function should itself return a stream of something and these streams are flattened by the flatMap() method, for instance given a stream of countries you can flatmap this stream to a stream of cities.

```java
record Country(List<City> cities) { }

List<Country> countries = ...;
List<City> cities = countries.stream()
        .flatMap(country -> country.cities().stream())
        .toList();
```
One last word, a mapping does not change the number of objects your stream processors, where a flatmap does. It can even produce zero elements
</details>

## 73. How is synchronization working?
<details>
  <summary>Short Answer</summary>

It works with the key held by the object you synchronize your block of code with
</details>
<details>
  <summary>Less Short Answer</summary>

This key is called the `monitor`, when a thread reaches a synchronized block or a method, it asks this object for its key. If the key is available, it takes it and run the code, if not it will have to wait until the key comes back. You absolutely want to avoid situations where the key never comes back usually because of `Deadlocks` but not only. In the case of an instance method, the object that holds the key is simply `this` and in the case of a static method, the object is the `class`.

One last word, try avoid synchronizing on objects that are public. That's a good rule to prevent Deadlocks, a situation you absolutely want to avoid
</details>

## 74. What is a generic type?
<details>
  <summary>Short Answer</summary>

A type that is parameterized over times
</details>
<details>
  <summary>Less Short Answer</summary>

Once defined along with the class, you can use this parameter in the class itself to define instance fields or instance methods. A single type can be parameterized over several types. Generics are massively used in athe JDK, all the collection framework, the stream API are using generics so you can check these classes to see how you can use them and how they were created.

```java
class Box<T> {
    void process() {
        Class c = T.class;  // NO !!
        T t = new T();      // NO !!
        T[] ts = new T[10]; // NO !!
    }
}
```

One last word, the type `T` is actually erased, it is replaced by object at runtime so there is a number of things you cannot do in your code. You cannot try to get the class of T because it will just return object, you cannot call `new T()` or `new Array<T>` neither
</details>

## 75. How can you stop a thread?
<details>
  <summary>Short Answer</summary>

You can't and you should not
</details>
<details>
  <summary>Less Short Answer</summary>

There are two methods on the thread class; `stop()` and `suspend()` that have been deprecated in Java 2 1998 that is more than 25 years ago. Now throw an `UnsupportedOperationException` so don't even think about using them. Why? the answer is actually not that simple. In short, they have been deprecated mainly for security reasons. Being able to stop a thread could put your application in an unpredictable state something you absolutely want to avoid.

One last word, you are not supposed to start no stop your threads by end anyway. The pattern you should be using is the `ExecutorService` pattern that takes care of your thread life cycle for you
</details>

## 76. How can you remove elements from a Stream?
<details>
  <summary>Short Answer</summary>

Use the `filter()` method
</details>
<details>
  <summary>Less Short Answer</summary>

Be careful though because the stream does not contain any object, it consumes objects from a source so saying removing objects from a stream is actually not correct what you're really doing is telling your stream do not process certain elements. Filtering uses a predicate that tests certain properties of the object and decide if it should be further processed or not. On this example, you only want to process the non-empty strings.

```java
Predicate<String> isEmpty = String::isEmpty;
Predicate<String> isNonEmpty = isEmpty.negate();
List<String> strings = ...;
List<String> nonEmptyStrings = strings.stream()
        .filter(isNonEmpty)
        .toList();
```

One last word, there are actually 2 other patterns that you can use to do that. `flatMap()` and `mapMulti()`. They are not really meant for that but in certain cases they can work better than filter
</details>

## 77. How is `Set.of()` working?
<details>
  <summary>Short Answer</summary>

It builds a set of its arguments if there are no duplicates among them
</details>
<details>
  <summary>Less Short Answer</summary>

The arguments are added one by one to an array of the right size using the `hashCode()` to detect any duplicates, if a duplicate is detected an `IllegalArgumentException` is immediately thrown. This method only requires one pass over your data because duplicates are not allowed in your arguments, it can create an array of the right size upfront making the memory conception minimal so all this is pretty optimal.

```java
public static void main(String[] args) {
    int[] ints = {1, 2, 3};
    Set<int[]> set = Set.of(ints);
    System.out.println(set.size()); // > 1
}
// or
public static void main(String[] args) {
    Integer[] ints = {1, 2, 3};
    Set<Integer> set = Set.of(ints);
    System.out.println(set.size()); // > 3
}
```

One last word, as usual be careful if you pass an array of primitive types because you will get a Set with a single element to your array which is usually not what you want.
</details>

## 78. How can you join Strings with a separator?
<details>
  <summary>Short Answer</summary>

You have a `join()` a factory method for that on the String class directly.

```java
List<String> strings = List.of();
var stringWithSeperator = String.join(",", strings);
```
</details>
<details>
  <summary>Less Short Answer</summary>

There are 2 overloads of this method, they both take a `delimiter` as a first argument and then you can pass a varargs or an array that's the first overloader or an iterable typically a collection and that's the second overload. If you need to add a prefix or a postfix to your string of character and then you can check the `StringJoiner.class` you can also reuse this StringJoiner if you have many strings to process.

```java

List<String> strings = List.of();
var joiner = new StringJoiner(",", "{", "}");
strings.forEach(joiner::add);
var stringWithSepPrefxSuffx = joiner.toString();
```

One last word, you can also check the collect `Collectors.joining()` pattern which does the same for the stream API. That's useful if you need to create this stream lazily without you having to buffer everything in a collection

```java
List<String> strings = List.of();
var stringWithSepPrefxSuffx = strings.stream()
        .collect(Collectors.joining(",", "{", "}"));
```
</details>

## 79. How can you modify your field using the Reflection API?
<details>
  <summary>Short Answer</summary>

You can use the `set()` method of the field class to do that

`Field.set(obj, value)`
</details>
<details>
  <summary>Less Short Answer</summary>

This method takes the instance you want to operate on and the value you want to fix, if you do not have access to this field because it is private for instance, you can still change it by calling its `Field.setAccessible(true)` passing true as an argument. It does not make the field public but suppresses the access controls made by the language.

One last word, you can actually mutate final fields in regular classes which this pattern which is really annoying but records are `protected` against that you cannot mutate them, one more reason to use records wherever you can
</details>

## 80. How can you declare a generic type on a Static Method?
<details>
  <summary>Short Answer</summary>

You need to define the type parameter along with the method declaration
</details>
<details>
  <summary>Less Short Answer</summary>

The type parameters you define on a class are only seen by the instance, fields and methods not by the static members. Suppose you have a Box<T> class and you want to define the static method copy(). To define the type parameter for this method you need to add it after the static keyword not also that if you have several static methods, each one needs to declare its own type parameter.

```java
class Box<T> {
    private T t;
    Box(T t) {
        this.t = t;
    }
    static <T> Box<T> copy(Box<T> box) {
        return new Box<>(box.t);
    }
}
```

One last word, you have many examples of that in the jdk, in the collections class for instance. They also use this word syntax question marks Super T `? super T` and question marks extensity `? extends` but that will be for another time
</details>

## 81. What does passing by value mean?
<details>
  <summary>Short Answer</summary>

It means that what you pass to a method is the value not a reference to this value
</details>
<details>
  <summary>Less Short Answer</summary>

The consequence is that if your method modify the argument it gets, the calling code does not see this modification, if what you pass is a primitive type changing it in your method does not change the value in a calling code. If what you pass is a reference changing the reference itself does not change it in a calling coder but if you change the content of the object reference then this change is seen in a calling code.

```java
class Scratch {
    public static void main(String[] arg) {
        Dog aDog = new Dog("Max");
        Dog oldDog = aDog;

        // we pass the object to foo
        foo(aDog);

        // aDog variable is still pointing to the "Max" dog when foo(...) returns
        System.out.println("3" + aDog.getName().equals("Max"));// true
        System.out.println("4" + aDog.getName().equals("Fifi"));// false
        System.out.println("5" + (aDog == oldDog)); // true
    }
    public static void foo(Dog d) {
        System.out.println("1" + d.getName().equals("Max")); // true
        // change d inside of foo() to point to a new Dog instance construct red with name member variable set to "Fifi"
        d = new Dog("Fifi");
        System.out.println("2" + d.getName().equals("Fifi")); // true
    }
}
class Dog {
    private String name;

    public Dog(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
/*
1true
2true
3true
4false
5true
*/
```

One last word, Java passes by value always no exception
</details>

## 82. What is the difference between an intermediate and a terminal operation?
<details>
  <summary>Short Answer</summary>

An intermediate operation returns a stream, the terminal operation returns something else including void
</details>
<details>
  <summary>Less Short Answer</summary>

The stream processes the data from the source only when it executes its terminal operation. If you do not call the terminal operation no data is processed, you can only call one intermediate or terminal operation on a given stream object. It makes the storing of a stream in a local variable useless.

One last word, some terminal operations do not need to call the intermediate operations of your stream. The reason why you should not do any side effect in an intermediate operations, there are situations where they will not be executed
</details>

## 83. What list can you pass to a method that takes a List of Number `List<Number>`?
<details>
  <summary>Short Answer</summary>

List<Number> is certainly not List<Integer> even though Integer extends Number
</details>
<details>
  <summary>Less Short Answer</summary>

Even if a Type U extends a type T, a `List<U>` does not extend the List<T>. The reason is that within the method that takes a list of numbers, you could add a float to that list but then if you pass a list of integers at runtime, you actually end up trying adding a float to a list of integers that would cause an exception.
```java
void process(List<Number> list) {
    list.add(3.14f); // Legal
}
List<Integer> ints = ...;
process(ints); // COMPILE ERROR
```
One last word, you could change your method and declare that it takes a list of question marks extends number(`List<? extends Number>`) and in that case you will be able to pass the list of Integer, Double and alike
```java
void process(List<? extends Number> list) {
  ...
}
List<Integer> ints = ...;
process(ints); // ok
```
</details>

## 84. What is a DeadLock?
<details>
  <summary>Short Answer</summary>

A situation where a first thread holds the lock and needs the second one to carry on its task and the second thread is holding that second lock and is waiting for the first one to carry on with its task
</details>
<details>
  <summary>Less Short Answer</summary>

This situation is really very bad, most of the time your solution would be to reboot your application, so you absolutely want to avoid it. It can also occur with the second lock that is outside of your application like in your database for instance.

One last word, one word of sound to avoid that never expose your locks as a public elements. Always use private fields to store your locks, it will help you most of the time but not always unfortunately.
</details>

## 85. How can you create an object instance of a given class using the Reflection API?
<details>
  <summary>Short Answer</summary>

There is a pattern for that called `getDeclaredConstructor()` that gives you a reference on the empty constructor of this class and called `newInstance()` on it.
</details>
<details>
  <summary>Less Short Answer</summary>

The pattern that consists including `newInstance()` directly on the class itself has been deprecated in Java 9 mostly because it does not handle exceptions properly. If your class does not have an empty constructor then this pattern throws a `NoSuchMethodException` exception.

```java
class Box {
    Box(String s) {
        // ...
    }
}

public static void main(String[] args) {
  var c = Box.class;
  var ctor = c.getDeclaredConstructor(String.class);
  Box box = ctor.newInstance("Hello");
  c.newInstance(); // @Deprecated(since="9")
}
```

One last word, you can also get a reference on the other constructors of your class by passing the parameters they take as classes to `getDeclaredConstructor()` method
</details>

## 86. What is the difference between a Collection and a List?
<details>
  <summary>Short Answer</summary>

A List is ordered, a Collection is not
</details>
<details>
  <summary>Less Short Answer</summary>

Ordered means that the order in which you iterate over the elements is stable from one iteration to the other and corresponds to the order in which you added the elements to your list. It is the case for all Lists because that's the specification but it's not the case for `HashSet` for instance and because the HashSet is a collection not all collections have this behavior. Adding elements to a HashSet may change the iteration order all the other elements so it's not even stable from one iteration to the other.

One last word, the consequence is that you can access the elements of your list using an index that wouldn't make sense for our Sets.
</details>

## 87. What is the difference between the `toList()` and collect `Collectors.toList()`?
<details>
  <summary>Short Answer</summary>

Both are terminal operations of the stream API. `Collectors.toList()` producers an Arraylist and `toList()` produces a Non-modifiable List.
</details>
<details>
  <summary>Less Short Answer</summary>

The fact that `Collectors.toList()` producers on ArrayList is actually not specified but it's the case. There are cases where `toList()` is actually more efficient, in a case where you know how many elements your stream is going to process, `toList()` can create an array of the right size up front, where `Collectors.toList()` relies on the automatic growing of your ArrayList.

One last word, the streamed `toList()` method produces a non-modifiable list that accepts null values, not all non-modifiable lists accept them `List.of()` doesn't for instance.
</details>

## 88. Can you compare Integers and Doubles with a Comparator of Numbers?
<details>
  <summary>Short Answer</summary>

Yes
</details>
<details>
  <summary>Less Short Answer</summary>

This is fine because what you are defining is a method that takes two parameters of type Number and it's fine to call it with any extension of number, actually you could use such a comparator to define the comparison between integers and floating point numbers for instance. Such a comparator is also okay to sort any list of integers of floating point numbers because all these types extended Number.

One last word, don't make your comparator a `Comparator<? extends Number>` because in that case you will not be able to call it with any other wrapper types. There is a good reason for that but that will be for another time
</details>

## 89. How can you model the Concurrent tasks in Java?
<details>
  <summary>Short Answer</summary>

You have two interfaces for that `Runnable` and `Callable`
</details>
<details>
  <summary>Less Short Answer</summary>

Both have functional interfaces so you can implement them with lambdas, neither of them take any parameter.

```java
Runnable runnable = () -> {doSomething();};
Callable<Integer> callable = () -> {return anInt();};
```

A Runnable does not return anything and does not throw any exception. A Callable on the other hand can return a value and throw an exception.

Runnable is the only task you can pass to the constructor all the builder of a thread. Callable and Runnable can be passed through an `ExecutorService` or `StructuredTaskScope`.

```java
var thread = Thread.ofVirtual().start(runnable);
ExecutorService service = ...;
service.submit(runnable);
service.submit(callable);
```

One last word, when you submit a task to an ExecutiveService, you get a Future object in return something we will talk more about in the future precisely
</details>

## 90. What is an Annotation?
<details>
  <summary>Short Answer</summary>

An interface with methods on which you can define default values
</details>
<details>
  <summary>Less Short Answer</summary>

```java
@Retention(RetentionPolicy.RUNTIME) // when
@Target({
  ElementType.FIELD,
  ElementType.METHOD,
  ElementType.CONSTRUCTOR
}) // where
@interface Range {
  int begin() default 0;
  int end();
}
```

You can define your own annotations easily with methods that may return default values, along with your annotation you need to define two things where you can add this annotation in your code and when you want to access it. There are currently 12 places where you can add an annotation for instance Fields, Classes, Methods or Parameters are among them then you can declare that you will need to use your annotation at runtime or only when your class is loaded or at compile time.

One last word, at Runtime you need to use the reflection API to get the annotations added to an element of your code, a technique used by many frameworks; Hibernate or SpringBoot just to name a few
</details>

## 91. What is a `? extends T`?
<details>
  <summary>Short Answer</summary>

It is a type called the wild card that has been created to extend a parameter's type by itself with an extension of its parameter
</details>
<details>
  <summary>Less Short Answer</summary>

Suppose you have two types `T` and `U` and `U extends T`, a class parameterized on U does not extend the same class parameterized on T. `Box<U> does not extend Box<T>`

```java
import java.util.List;

static List<Long> convert(List<Number> numbers) {
    return numbers.stream()
            .map(Number::longValue)
            .toList();
}

public static void main(String[] args) {
  List<Double> doubles = List.of();
  
  // DOES NOT COMPILE !!!
  var longs = convert(doubles);
  // Required type: List<Number>
  // Provided: List<Double>
}
```

Look at this convert method, it could accept a list of double. We can fix that with a list of question mark extends number `? extends Number` because list of double extends a list of question mark extend number.

```java
import java.util.List;

static List<Long> convert(List<? extends Number> numbers) {
    return numbers.stream()
            .map(Number::longValue)
            .toList();
}

public static void main(String[] args) {
  List<Double> doubles = List.of();
  
  // OK
  var longs = convert(doubles);
}
```

One last word, this technique is extensively used in a collection framework and in along the world, comparators, consumers, predicates functions their old use wild cards.

```java
public static <T> void sort(List<T> list, Comparator<? super T> c) {}
default Consumer<T> andThen(Consumer<? super T> after) {}
default Predicate<T> and(Predicate<? super T> other) {}
default <V> Function<V, R> compose(Function<? super V, ? extends T> before) {}
```
</details>

## 92. What is a Constructor?
<details>
  <summary>Short Answer</summary>

An element of a class that is called when an instance of this class is built
</details>
<details>
  <summary>Less Short Answer</summary>

Be careful, because the `Constructor` is not a method. It does not have a written type and is not compiled in the same way. You can have several overloads of a constructor in a class, all they need is declare different parameters. Constructors can throw exceptions so if you want to do some validation to prevent corrected objects to be built, you can do that in your Constructor.

One last word, you can write compact constructors in Records which is a very nice and very simple syntax to write constructors that only do some validation, one more reason to use Records wherever you want
</details>

## 93. What is a short-circuit method?
<details>
  <summary>Short Answer</summary>

Several methods from the Stream API are called short-circuit methods
</details>
<details>
  <summary>Less Short Answer</summary>

These method may interrupt the conceptions of the elements of your source. There are 2 intermediate operations `limit()` and `takeWhile()` and 5 terminal operations of `allMatch()`, `anyMatch()` and `noneMatch()` plus `findFirst()` and `findAny()` because elements are processed lazily and one by one by the stream API, short-circuit operations can prevent some elements to be read from your source which may be really bad if you are doing some side effects in your intermediate operations.

One last word, doing side effects in a stream intermediate or terminal operations is always a bad idea. Don't do it
</details>

## 94. What is an Atomic variable?
<details>
  <summary>Short Answer</summary>

A wrapper on a primitive type or a reference with methods to mutate it in a thread safe and efficient way
</details>
<details>
  <summary>Less Short Answer</summary>

The atomic variables are actually mappings of CPU operations also called `CASing` operations. CASing means `C`ompare `A`nd `S`wap. For instance, on atomic integer you can call `increment()` and `get()` that will increment the internal value and return it atomically. This operation is thread safe, it does not rely on synchronization which prevents thread contention.

One last word, atomic references are used to implement two thread safe structures from the collection framework; `ConcurrentSkipListMap` which is a Map and `ConcurrentSkipListSet` which is a Set, all these without any synchronization
</details>

## 95. What is a Record?
<details>
  <summary>Short Answer</summary>

Something you should use all the time
</details>
<details>
  <summary>Less Short Answer</summary>

It is a class that carries some immutable state declared along with its declaration. This state is called the Components of your record. A record cannot extend anything and cannot be extended but it can implement any interface. It cannot declare an instance field, static fields are okay and it can declare any method. The compiler gives you a constructor accesses that you can rewrite yourself and `toString()`, `equals()` and `hashCode()` for free. You can do some validation and deserialization, calls this constructor so no corrupt record in your application.

```java
record Range(int begin, int end) implements Serializable {
    Range {
        if (begin > end) {
            throw new IllegalArgumentException("...");
        }
    }
    int size() {
        return end - begin;
    }
}
```

One last word, use records wherever and whenever you can
</details>

## 96. How can you invoke a method using the Reflection API?
<details>
  <summary>Short Answer</summary>

There is an `invoke()` method in the `Method.class`
</details>
<details>
  <summary>Less Short Answer</summary>

We can get a specific method of a class with the `getMethod()` or `getDeclaredMethod()` of the class named Class. You need to pass the name of the method you want along with the types of its parameters. When you have a method object all you need to do is call the invoke() method passing first the object on which you want to invoke this method and then the arguments needed by this method. We can invoke a private method from outside the class by first calling the `setAccessible(true)` which removes the visibility checks.

```java
import java.lang.reflect.Method;

public static void main(String[] args) {
    var c = String.class;
    Method indexOf = c.getMethod("indexOf", String.class);
    var message = "Hello world";
    var index = indexOf.invoke(message, "world");
    // output: 6
}
```

One last word, you also have another pattern to do that that uses the method and all class but that would be for another time oh
</details>

## 97. What is a ConcurrentModificationException?
<details>
  <summary>Short Answer</summary>

An exception raised when you modify your collection while iterating over it
</details>
<details>
  <summary>Less Short Answer</summary>

Be careful because despite the name, it has nothing to do with concurrent programming. Removing elements from a collection while iterating over it is generally not a great idea. There is a `remove()` method on iterator that you can use just make sure that it is supported by your implementation if what you need is to remove elements using your predicate for instance, you can use the `removeIf()` method that does exactly that.

```java
import java.util.ArrayList;
import java.util.List;

public static void main(String[] args) {
    var list = List.<String>of("1", "2");
    list = new ArrayList<>(list);
    var iterator = list.iterator();
    while (iterator.hasNext()) {
        var s = iterator.next();
        list.remove(s); // Exception in thread "main" java.util.ConcurrentModificationException
        list.removeIf(String::isEmpty);
        if (s.isEmpty()) {
            iterator.remove();
        }
    }
}
```

One last word, some implementations of collection can be okay with removing elements while iterating over them, especially the concurrent ones like `ArrayBlockingQueue` or `ConcurrentLinkedQueue` so be sure to check the javadoc on this one
</details>

## 98. What is a Collector?
<details>
  <summary>Short Answer</summary>

An object provided by the Stream API that you can use to reduce streams using the `collect()` method
</details>
<details>
  <summary>Less Short Answer</summary>

A collector is an implementation of the `Collector` interface, you can implement this interface yourself. You also have a collector's factory class with plenty of pre-built collectors that should cover most of your needs. You can do many things with collectors; you can create any sort of collections or maps, you can group your stream elements using keys and gather them in maps or you can join them in strings of characters. You even have collectors that can map, filter or flatMap the elements of your stream.

One last word, sometimes the stream API uses DownStream Collectors, this is a way to compose collectors but that will be for another time
</details>

## 99. What is a Daemon Thread?
<details>
  <summary>Short Answer</summary>

A Thread
</details>
<details>
  <summary>Less Short Answer</summary>

When you create a thread, you can decide to set its daemon property to true, the JVM will start its shutdown sequence if it does not have any more non-daemon thread running. The thread main for instance that runs your main method is a non-demand thread so when you exit your main method the JVM shuts down. Non-Daeman thread keep your JVM alive that can be created in ExecutorServices for instance so don't forget to shut them down or your JVM will never shut down. 2 examples of the Daemon thread; the ones that are running your Garbage Collector or your Just In Time(`JIT`) compiler.

One last word, you can set the daemon property of a platform thread but a virtual thread is always a daemon thread
</details>

## 100. What is a Race Condition?
<details>
  <summary>Short Answer</summary>

A race condition occurs when two threads are writing and reading the same variable at the same time
</details>
<details>
  <summary>Less Short Answer</summary>

This is a situation you need to take care of because it can put your application in an inconsistent state. Suppose that you are incrementing a simple counter, you first read its value increment it and write it back if two threads are doing that in two different calls of your CPU. They may be reading the same value and what you will see is one incrementation instead of two. To prevent race conditions, you need to guard your variables with synchronization or use atomic variables.

One last word, in Java, race conditions can only happen on the fields of your classes not on local variables. It can be different in other languages
</details>

## 101. How can you check if a class is an extension of another?
<details>
  <summary>Short Answer</summary>

There is a method for that in a `Class.class`
</details>
<details>
  <summary>Less Short Answer</summary>

This method is called `isAssignableFrom()` you call it on a class instance which could represent an interface by the way and pass another class instance as an argument. `isAssignableFrom()` checked if an instance of the argument class you pass can be assigned to a variable of the type you are calling this method on, for instance you can check if you can assign a string object to a variable of type comparable with the following code.

```java
public static void main(String[] args) {
    var v = Comparable.class;
    var checked = String.class;
    boolean b = v.isAssignableFrom(checked);
    // the compiler knows b is true!
    // use it for types unknown
    // at compile time
}
```

One last word, this is a method that you should use with types that you don't know at compile time, if you do then you probably don't need it
</details>

## 102. What is the type `? super T`?
<details>
  <summary>Short Answer</summary>

This type represents all the types that are super types of T
</details>
<details>
  <summary>Less Short Answer</summary>

This is the kind of type you need when you need to define the type of an object that you consume. Suppose that you have a list of polygon objects, you know that all the objects of this list can be cast to the polygon type. Processing them with a consumer of shape will then be okay thus the forEach() method takes a consumer that can consume any type that is a super type of polygon and the same goes for methods that take functions, these functions are declared to take `? super T`

```java
interface Polygon extends Shape {}
List<Polygon> list = ...;
Consumer<Shape> consumer = ...;
list.forEach(consumer); // OK

void forEach(Consumer<? super Polygon>){...}
```

One last word, as this type can be any super type of T, the only type you can assign it to is the `Object` type
</details>

## 103. What does static mean?
<details>
  <summary>Short Answer</summary>

Static can be added on a field or a method declaration, it means that this member is attached to the type not to an instance
</details>
<details>
  <summary>Less Short Answer</summary>

Static fields can be defined on classes and static methods can be added to classes or interfaces because a static member belongs to a class, you should use it directly with the class name, if it is a field all your instances share this field so using immutable static fields usually means trouble. If you invoke a static member with an instance, the compiler will replace that instance with the class, meaning that you can read a static field using a null instance without throwing a `NullPointerException`

```java
public static void main(String[] args) throws Exception {
    Shape shape = null;
    shape.print(); // prints: Hello World
}

class Shape {
    static {
      System.out.println("From static");
    }
    public static void print() {
        System.out.println("Hello World");
    }
}
```

One last word, you can also define static blocks in your class but please stay away from that this is an anti-pattern
</details>

## 104. What is a DownStream Collector?
<details>
  <summary>Short Answer</summary>

A Collector!
</details>
<details>
  <summary>Less Short Answer</summary>

Most of the time, you will create your collectors with one of the factory methods of the `Collector`s class, some of these methods takes a collector as a last parameter called the downstream collector. This collector is used to further process your data for instance the `groupingBy()` collector groups your elements using a key. The downstream collector that you can provide is used to collect these groups so you can put them in a list, a set, you can join them or you can even create another map.

One last word, some factory methods always take a downstream collector. This is the case for mapping, filtering or flatMapping methods. They actually defined intermediate operations that need this downstream collector to model the terminal operation that will process your stream
</details>

## 105. Why is `Thread.stop()` deprecated?
<details>
  <summary>Short Answer</summary>

Because it is unsafe
</details>
<details>
  <summary>Less Short Answer</summary>

Being able to interrupt the thread could lead to several problems in your application. If your thread is holding a synchronization key for instance because it is currently updating some shared in-memory structure, interrupting it would free these keys and expose this structure leaving it in a state that could be inconsistent and the same goes if your thread is holding a system resource that needs to be closed. Not closing that resource properly could lead to a resource leaking, a situation you want to avoid.

One last word, this method has been deprecated in Java 1.2 in 1998 that was a long time ago. It is now throwing an `UnsupportedOperationException` to make sure that you don't call it
</details>

## 106. What does `Comparable` mean?
<details>
  <summary>Short Answer</summary>

It means that you can compare these objects without a `Comparator`
</details>
<details>
  <summary>Less Short Answer</summary>

There are 2 mechanisms in Java to compare objects and tell if one is greater than the other. First, you can create a comparator that takes two objects and return an int and then you can implement the `Comparable` interface that basically does the same, you pass another object that returns an int. This int should be positive if this is greater than other, negative if not and zero if these objects are equal. With a comparator, you can compare objects with another semantic than the one implemented by comparable.

```java
record User(String name, int age) implements Comparable<User> {
  int compareTo(User other) {
    return Integer.compare(this.age, other.age);
  }
}
Comparator<User> cmp = (u1, u2) -> u1.name().compareTo(u2.name());
// or
Comparator<User> cmp2 = Comparator.comparing(User::name);
```

One last word, remember that comparison should be symmetric and transitive, if it is not, you may stumble upon the infamous comparison method violates its general contract error message
</details>

## 107. How can you create a prefilled maps?
<details>
  <summary>Short Answer</summary>

There is a method for that `Map.of()`
</details>
<details>
  <summary>Less Short Answer</summary>

`Map.of()` is super simple to use. Just call it and pass a key, it's value then the next key and its value and again up to 10 entries.

```java
// Up to 10 key / value pairs
var map1 = Map.of(1, "one", 2, "two");
```

Past the 10 entries, you need to change the pattern because you cannot overload this kind of method with a vararg so another method has been added `Map.of()` entries that takes a vararg of entries that you can create with the `Map.entry()`. The map you get is `non-modifiable` and the entry objects are also `non-modifiable`, you cannot pass the same key twice if you do that you will get an exception.

```java
// No Limit
var e1 = Map.entry(1, "one");
var e2 = Map.entry(2, "two");
var e3 = Map.entry(2, "two"); // Exception in thread "main" java.lang.IllegalArgumentException: duplicate key: 2
var map2 = Map.ofEntries(e1, e2, e3);
```

One last word, none of these method except null, neither for the key nor the value know the entry. Really, why would you do that?
</details>

## 108. What is the return type of `max()`?
<details>
  <summary>Short Answer</summary>

An Optional
</details>
<details>
  <summary>Less Short Answer</summary>

Whether you like `Optional` or not or think they are good thing or not, in that particular case this is what you need. Suppose you compute the max of a first stream and then the max of a second stream and then you need to max all the elements of both streams what you expect is that the max of both maxes give you the max of all your elements and it will. Unless, one of the stream is empty if you choose to handle this case by returning null then you cannot handle primitive types and choosing your default value will not work neither `Integer.MIN_VALUE` will not work for instance because you can convert this int to a longer.

One last word, there are several very interesting patterns to process optionals that will make Optionals look like stream but that will be for another time
</details>

## 109. What is a `Future`?
<details>
  <summary>Short Answer</summary>

An object to communicate with the task that is being executed in another thread
</details>
<details>
  <summary>Less Short Answer</summary>

You get a Future object when you submit a Runnable or Callable to an ExecutorService. An ExecutiveService immediately gives you a future object but it will execute your task in another thread sometimes in a future. At this point, you can use this Future to check if your task is done and to get either the result it produced or the exceptions that was thrown. There is an overload of the `get()` method that takes a timeout, this may be safer to prefer this pattern rather than a regular get.

```java
V get(long timeout, TimeUnit unit) throws InterruptedException, ExecutionException, TimeoutException;
```

One last word, starting with Java 21, you can call `state()` that returns running Success, Failed or Cancelled.
</details>

## 110. What does multiple inheritance mean?
<details>
  <summary>Short Answer</summary>

It means trouble
</details>
<details>
  <summary>Less Short Answer</summary>

Multiple inheritance is an object-oriented notion. There are 3 types of inheritance.
- Inheritance of type(`Type Inheritance`) and Java supports multiple inheritance of type, as a class can implement as many interfaces as you need.
- Inheritance of behavior(`Behavior Inheritance`) and Java supports it also. Concrete methods are in inherited from a super class and also from default methods in interfaces and you may run into issues with this one if you implement two interfaces with the same default methods.
```java
interface A {
    default void print() {
        System.out.println("A");
    }
}
interface B {
    default void print() {
        System.out.println("B");
    }
}
class AB implements A, B {
    public void print() { // need to override
        A.super.print(); // specific interface should be defined
    }
}
```
- And the last one is the inheritance of state(`State Inheritance`) that is not supported by Java.

One last word, favor `Object Composition Over Class Inheritance` that's the introduction of `GoF` must read
</details>

## 111. What is the no-arg empty constructor?
<details>
  <summary>Short Answer</summary>

A constructor that the compiler adds to a class when you don't declare any
</details>
<details>
  <summary>Less Short Answer</summary>

If you create a class and you don't provide your own constructor, the compiler will add one for you because every class should have at least one constructor. This constructor does not do anything and does not take any parameter thus its name the `no-arg constructor`. This may be confusing because if you create a constructor later, then this empty constructor is not added anymore and that can create compiler errors somewhere else in your application. Of course, you can still add one by hand to fix that.

One last word, many frameworks that rely on `Reflection` are using this empty no-arg constructor so there are many cases where it is wise to keep it
</details>

## 112. What is Iterable?
<details>
  <summary>Short Answer</summary>

An interface
</details>
<details>
  <summary>Less Short Answer</summary>

This interface is extended by collection so it is actually the base interface of many interfaces of the `Collections Framework`. It has only one abstract method `iterator()` so you can implement it with a lambda expression. All iterables can be used in a `forEach()` pattern and this is very handy. If you already have an iterator in your application, you can use it to create an iterable and then go through all the values of this iterator using your iterable in this forEach pattern.

```java
Iterable<Integer> iterable = () -> itr;
for (int index: iterable) {
  System.out.println("index = " + index);
}
// or
iterable.forEach(System.out::println);
```

One last word, iterable also declares a `forEach()` method so you can also go through the values generated by your iterator using this pattern
</details>

## 113. What does `Thread.interrupt()` do?
<details>
  <summary>Short Answer</summary>

It doesn't do what you think
</details>
<details>
  <summary>Less Short Answer</summary>

`Thread.interrupt()` tries to interrupt your thread in two ways; First, it can make one of your call to throw an exception if your task is blocked on the call to `sleep()`, `wait()`, `notify()` then this method immediately throws an `InterruptedException`, same if you're waiting for a permit() from a `Semaphore` for there are also many cases where if you are waiting for some data on an I/O request for instance and an exception will also be thrown. In all the other cases, your task should regularly call the interrupted method and if it returns true then it is your responsibility to finish your task as soon as possible.

One last word, don't try to handle your threads yourself. There are ExecutorServices and `ForkJoinPool` especially for that
</details>

## 114. What is the first thing that a constructor do?
<details>
  <summary>Short Answer</summary>

It calls another constructor
</details>
<details>
  <summary>Less Short Answer</summary>

This other constructor can be a constructor from the same class or from the super class. If you don't write any call to any constructor then the compiler adds a call to the empty constructor of your super class so if this empty constructor does not exist in a super class then you will get a compile error. You can also call a specific constructor, it can be a call to `this()` that calls a constructor from the same class or a call to `super()` that calls a constructor from the super class. Constructing an object requires that you call all the constructors from object to your class.

One last word, this may be annoying when you need to validate your arguments and it actually may change in a future but that will be for another time
</details>

## 115. What are the 4 fundamental functional interfaces in Java?
<details>
  <summary>Short Answer</summary>

`Consumer`, `Supplier`, `Function` and `Predicate`
</details>
<details>
  <summary>Less Short Answer</summary>

These are the 4 Functional Interfaces from the `java.util.function` package.

- A `consumer` takes an argument and doesn't return anything.
  - ```java
    Consumer<String> consumer = s -> System.out.println(s);
    ```
- A `supplier` doesn't take anything and returns something.
  - ```java
    Supplier<Double> supplier = () -> Math.PI;
    ```
- A `function` takes something and returns something else.
  - ```java
    Function<String, Integer> function = s -> s.length();
    ```
- A `predicate` is a function that returns a Boolean.
  - ```java
    Predicate<String> predicate = i -> i % 2 == 0;
    ```

Then there are a number of variations BiConsumer, BiFunction, BiPredicate that take two arguments. They are also UnaryOperator or BinaryOperator as well as specialization for primitive types for instance IntConsumer.

```java
BiConsumer<String, String> biConsumer = (s1, s2) -> System.out.println(s1 + s2);
BiFunction<String, String, Integer> biFunction = (s1, s2) -> s1.indexOf(s2);
BiPredicate<Integer, Integer> biPredicate = (i1, i2) -> i1 > i2;

UnaryOperator<String> unary = s -> s.toUpperCase();
//UnaryOperator<String> unary = String::toUpperCase;
BinaryOperator<String> binary = (s1, s2) -> s1 + ", " + s2;

IntConsumer intConsumer = i -> System.out.println(i);
// IntConsumer intConsumer = System.out::println;
DoubleSupplier doubleSupplier = () -> Math.PI;
ToIntFunction<String> toIntFunction = s -> s.length();
//ToIntFunction<String> toIntFunction = String::length;
IntPredicate intPredicate = i -> i % 2 == 0;
```

One last word, there is also `Runnable` that does not take any argument and that does not return anything, it fits nicely in this family
</details>

## 116. What is an Enumeration?
<details>
  <summary>Short Answer</summary>

A class with a set of instances declare that `Compile Time`
</details>
<details>
  <summary>Less Short Answer</summary>

Enumerations are interesting when you know that a class can only have a limited number of instances. Enumerations can have a state, even a mutable state, Why would you do that?, and you can declare a constructor for them. Your Enum class is `final` and extends the class Enum so your enumeration cannot extend anything and cannot be extended but it can implement interfaces.

```java
interface IMonth {
    String fetchName();
}
enum Months implements IMonth {
  JANUARY, FEBRUARY, MARCH, APRIL, MAY, JUNE, JULY, AUGUST, SEPTEMBER, OCTOBER, NOVEMBER, DECEMBER;
    public String fetchName() {
        return this.name();
    }
}

enum Month {
  JANUARY(31), ...;
  private final int length;
  Month(int length) {
    this.length = length;
  }
  public int length() {
    return this.length;
  }
}
```

One last word, because you cannot create any more instance of an enumeration at runtime, using enumerations is the preferred pattern to create singleton. You can see examples of that in the naturalOrder() factory method of the comparator interface `Comparator.naturalOrder()`
</details>

## 117. How is `List.sublist()` working?
<details>
  <summary>Short Answer</summary>

It gives you a mutable view of a given list
</details>
<details>
  <summary>Less Short Answer</summary>

It's actually a nifty feature and probably overlooked. First, it's a list so you can use it as such but it's also a mutable view so you can use it to manipulate the first list for instance you can insert a list in another one at a given place by calling sublist() passing the same index for the fromIndex and the toIndex and calling `addAll()` on this view or you can clear a range of indexes from a list with `sublist(...).clear()`

```java
var l2 = List.of(4, 5, 6);
var l1 = List.of(1, 2, 3);

var list = new ArrayList<>(l2);
System.out.println(list);
// > [4, 5, 6]

list.subList(0, 0).addAll(l1);
System.out.println(list);
// > [1, 2, 3, 4, 5, 6]

list.subList(1, 5).clear();
System.out.println(list);
// > [1, 6]
```

One last word, if what you need is to select a range of indexes and don't need the rest of the list anymore then you should copy this sublist because if you don't, you will still have the original list in memory which can be an overhead

```java
var list = List.of(1, 2, 3, 4, 5, 6);
// keeps list in memory
var sub = list.subList(2, 4); // [3, 4]
// keeps only what you need
var sub = List.copyOf(list.subList(2, 4)); // [3, 4]
```
</details>


<details>
  <summary>Short Answer</summary>

A class with a set of instances declare that `Compile Time`
</details>
<details>
  <summary>Less Short Answer</summary>

Enumerations are interesting when you know that a class can only have a limited number of instances. Enumerations can have a state, even a mutable state, Why would you do that?, and you can declare a constructor for them. Your Enum class is `final` and extends the class enum so your enumeration cannot extend anything and cannot be extended but it can implement interfaces.

```java
enum Months {
  JANUARY, FEBRUARY, MARCH, APRIL, MAY, JUNE, JULY, AUGUST, SEPTEMBER, OCTOBER, NOVEMBER, DECEMBER
}

enum Month {
  JANUARY(31), ...;
  private final int length;
  Month(int length) {
    this.length = length;
  }
  public int length() {
    return this.length;
  }
}
```

One last word, because you cannot create any more instance of an enumeration at runtime using enumerations is the preferred pattern to create singleton. You can see examples of that in the natural order factory method of the comparator interface `Comparator.naturalOrder()`
</details>

## 118. How can you create a map to hold 20 elements?
<details>
  <summary>Short Answer</summary>

There is a factory method for that `HashMap.newHashMap()`
</details>
<details>
  <summary>Less Short Answer</summary>

Creating a map with a given capacity is more complex than it seems. Hashmap carries an internal array and when the number of used cells reaches a certain level then the content of the array is copied in a larger array which is costy and this is the reason why it may be interesting to create an array that is large enough up front but then there is some math to do to get this size that has been written in this factory method.

```java
var map1 = HashMap.newHashMap(24); // initialCapacity = 32 => ((int) Math.ceil(24 / (double) 0.75f))
var map2 = LinkedHashMap.newHashMap(36);

// Doesn't do what you need!
var map3 = new HashMap(24); // initialCapacity = 24
```

One last word, be careful because HashMap has also a constructor that takes an int that is a size but this size is actually the size of the internal array which may be too small to store all the key value pairs you have
</details>

## 119. How can you use FlatMap to filter a stream?
<details>
  <summary>Short Answer</summary>

Your `flatMap()` method should return an empty stream when you don't want to pass the corresponding value
</details>
<details>
  <summary>Less Short Answer</summary>

There are cases where filtering a stream may be too complex or too costly. This is the case on this example where you should filter on the fact that analyzing your string should not throw a `NumberFormatException`. The complete code is complex and really not nice. Using a flatMap and returning an empty stream if the result cannot be computed is probably better.

```java
var intsAsStrings = List.of("1", "2", "3");
var intsAsStrings = List.of("1", "2", "3");
var ints = intsAsStrings.stream()
                      .map(s -> Integer.parseInt(s))
                      .toList();
System.out.println(ints);
// > [1, 2, 3]
```

```java
var intsAsStrings = List.of("1", "2", "one", "3");
var intsAsStrings = List.of("1", "2", "3");
var ints = intsAsStrings.stream()
                        .flatMap(s -> {
                          try {
                            return Stream.of(Integer.parseInt(s));
                          } catch (NumberFormatException e) {
                            return Stream.of();
                          }
                        })
                        .toList();
System.out.println(ints);
// > [1, 2, 3]
```

One last word, there is actually another method to do the same thing that will save the construction of this stream object. It's the `mapMulti()` method that was added in the JDK16
</details>

## 120. What does Reentrant mean for synchronization?
<details>
  <summary>Short Answer</summary>

It means that when your thread already has the lock of a synchronized block, it can enter it
</details>
<details>
  <summary>Less Short Answer</summary>

When it needs to enter a synchronized block, your thread asks for the key of the object that is used to guard this block. If the key is not there, your thread is blocked until the key becomes available again. There are cases where you make call a synchronized method from a first synchronized method of the same class or from a subclass and in that case your thread is already holding that key so it can execute this code without having to wait.

```java
class A {
  synchronized void a1() {
    // synchronized on this
    a2();
  }
  synchronized void a2() {
    // synchronized on this
  }
}
class B extends A {
  synchronized void b() {
    // synchronized on this
    a2();
  }
}
```

One last word, the synchronization classes from `java.util.concurent` are also reentrant. This is the case for the `ReentrantLock.class` as its name may suggest
</details>

## 121. What does shallow copy mean?
<details>
  <summary>Short Answer</summary>

It means duplicating an object but not the object this object has references
</details>
<details>
  <summary>Less Short Answer</summary>

There are cases where it makes sense to shadow copy an object and others where it can be actually dangerous: The rule of thumb that will always work is the following if the related object is non-modifiable like a string then there is no need to duplicate it. In that case shallow copy is okay but if your related object is an ArrayList for instance, it means that anyone with a reference to this ArrayList can modify it and thus modify the internal state of your object and most of the time this is not what you want.

One last word, you can protect your objects against that with the defensive copy pattern but that will be for another time
</details>

## 122. What is the `Vector`?
<details>
  <summary>Short Answer</summary>

Something you should not be using anymore
</details>
<details>
  <summary>Less Short Answer</summary>

A vector is an old API from before the `Collections Framework`. This was before Java 2 released in 1998, with Java 2 the Vector class has been refactored to be included in the Collections framework. A vector is `thread safe` but in a very basic way. All its methods are synchronized including `size()` or `isEmpty()` which is actually not that great. If you do not need thread safety, you can safely use ArrayList instead and if you do, well there are better implementations depending on your use case.

One last word, this Vector class has nothing to do with the vector API which gives you access to the cmd parallel computing capacity of your CPU but that will be for another time
</details>

## 123. What is the difference between `Runnable` and `Callable`?
<details>
  <summary>Short Answer</summary>

Both are used to model tasks in concurrent programming
</details>
<details>
  <summary>Less Short Answer</summary>

```java
@FunctionalInterface
interface Runnable {
  void run();
}

@FunctionalInterface
interface Callable<V> {
  V vall() throws Exception;
}
```

A `Runnable` is a task model introduced in the first versions of java. It doesn't take any argument and does not return anything. `Callable` was added in Java 5 in 2004 as part of the `java.util.concurrent` API. A Callable doesn't take any argument but it does return something and can throw an exception. Runnable is the only one that can be passed to thread creation including with the factory methods added in Java 21 where both can be passed to `ExecutorService`s and `ForJointPool`s.

```java
Runnable runnable = ...;
Callable callable = ...;

ExecutorService service = ...;
service.submit(runnable);
service.submit(callable);

ForkJoinPool pool = ...;
pool.submit(runnable);
pool.submit(callable);
```

One last word, `StructuredTaskScope` only accept Callables, we will talk more about that later

```java
StructuredTaskScope scope = ...;
Callable callable = ...;
scope.fork(callable);
// can't pass a Runnable
```
</details>

## 124. Can you create a stream from an Iterable?
<details>
  <summary>Short Answer</summary>

Yes
</details>
<details>
  <summary>Less Short Answer</summary>

There is actually an API to do that. Most of the time you will create streams from collections using the `Collection.stream()` method but sometimes all you have is an iterable in that case creating a collection or an array and then opening a stream on it would be a waste of memory. You can call `StreamSupport.stream(...)` pass a spliterator that you can create directly from your Iterable and then false because you don't want to mess with parallel streams.

```java
Iterable<String> iterable = ...;
Stream<String> stream = StreamSupport.stream(
        iterable.spliterator(),
        false // parallel?
);
```

One last word, in the case your Iterable produces an unlimited amount of data then a stream can handle that with some short-circuit operations where trying to build a collection would just break your application
</details>

## 125. How is `CopyOnWriteArrayList` working?
<details>
  <summary>Short Answer</summary>

Well, as the name suggests it copies its internal array on each write operation
</details>
<details>
  <summary>Less Short Answer</summary>

`CopyOnWriteArrayList` is a thread save list that is interesting if what you have is
mostly read operation. This class works in that way; First, the internal array is duplicated and then mutated within a synchronized block then the internal reference to this array is updated because this reference is volatile reading does not need to be synchronized so no contention on read operation. The major of ahead is the array duplication.

```java
public boolean add(E e) {
    synchronized (lock) {
        Object[] es = getArray();
        int len = es.length;
        es = Arrays.copyOf(es, len + 1);
        es[len] = e;
        setArray(es);
        return true;
    }
}
public E get(int index) {
    return (E) array[index];
}
```

One last word, there is also a `CopyOnWriteArraySet` that actually wraps a `CopyOnWriteArrayList` so same warnings on this one
</details>

## 126. What is the switch statement?
<details>
  <summary>Short Answer</summary>

And old stuff that got some attention recently
</details>
<details>
  <summary>Less Short Answer</summary>

`Switch` used to be a statement that would work on a selector variable that could be an integer type not a long, an Enum or a String of characters. This selector could not be null. It can now be an expression also can accept any object including nulls for this selector and can accept patterns and guarded patterns for the case labels. It can even check for exhaustiveness and can prevent fall through so in one word, it has been fixed and is now much more useful. It could even handle exceptions as case labels in a future.

One last word, switch expressions are now part of what is called Data Oriented Programming in Java but that will be for another time
</details>

## 127. What is the difference between an `Exception` and an `Error`?
<details>
  <summary>Short Answer</summary>

`Exceptions` are for your application, `Errors` are for the JVM
</details>
<details>
  <summary>Less Short Answer</summary>

In many cases you need to handle exceptions explicitly, if your exception is a `RuntimeException` which is an extension of the Exception class then you don't. Errors are mostly used to tell you that something went wrong in a JVM, some of them are thrown when the JVM is loading your classes so even before running them. That's the case for the `ClassFormatError`, `NoSuchMethodError`, `AbstractMethodError` or `ClassCircularityError`.

One last word, here are examples of errors that will put an end to your application `StackOverflowError`, `OutOfMemoryError`. There is even an `UnknownError` but I never saw it to be honest
</details>

## 128. What is a Red Black Tree?
<details>
  <summary>Short Answer</summary>

A data structure implemented by the `TreeMap` class
</details>
<details>
  <summary>Less Short Answer</summary>

`TreeMap` is actually an implementation of `NavigableMap` that extend `SortedMap` and since Java 21 `SequencedMap`. A Red Black Tree is a data structure that stores its element in a binary tree and keeps them sorted using a Nifty Node Reorganization algorithm. TreeMap keeps its key value pairs sorted by key while you're adding or removing them so when you iterate of them they are already sorted.

One last word, on the one hand a Red Black Tree is a very efficient data structure as most of the operations are `log(n)`. On the other hand, it's a reference based data structure so pointer chasing will not play nice with it
</details>

## 129. What are the visibility modifiers for members?
<details>
  <summary>Short Answer</summary>

`private`, `protected` and `public`
</details>
<details>
  <summary>Less Short Answer</summary>

There is also a fourth one which consists in not putting any modifier; `package private`. A private member can only be accessed from the class itself. A public member can be accessed from everywhere and can be limited by your module system. Protected can be accessed from the extending classes and from other classes within the same package. No modifier means that you can access them from the same package.

One last word, without the module system you can create a class in a package from any other jar that can give you access to all the protected and package private members so the two levels you should really rely on are private and public
</details>

## 130. What is a Sequenced Collection?
<details>
  <summary>Short Answer</summary>

An interface added to the Collections Framework
</details>
<details>
  <summary>Less Short Answer</summary>

This interface was added in Java 21 to fill a gap there was between Lists and SortedSets. Sequence collections allow you to ask for the first or last element of a collection and to remove it or add it if the collection is modifiable. You can also ask for a reverse view on the content of the collection.

```java
public interface SequencedCollection<E> extends Collection<E> {
  E getFirst();
  E getLast();

  void addFirst(E e);
  void addLast(E e);

  E removeFirst();
  E removeLast();

  SequencedCollection<E> reversed();
}

```

One last word, you also have `SequenceMap` and `SequenceSet` that extend `SequenceCollection` with a `reverse()` method that returns itself a SequencedSet

```java
public interface SequencedSet<E> extends SequencedCollection<E>, Set<E> {
    SequencedSet<E> reversed();
}
```
</details>

## 131. What does Encapsulation mean?
<details>
  <summary>Short Answer</summary>

It means no public instance fields in your classes
</details>
<details>
  <summary>Less Short Answer</summary>

The internal state of your class should be accessed only through accessors to modify it or to read it. One of the reason is that your code only depends on the public methods of its collaborator objects not on their internal implementation meaning that you can change it without changing their client code. Encapsulation is usually an object concern but you can also apply this principle to apis or libraries that you only depend on using their interface.

```java
class User {
    // private state
    private String name;
    
    // public accessors
    public String getName() {
        return this.name;
    }
    public void setName(String name) {
        this.name = name;
    }
}
```

One last word, even though Records are unmodifiable, you still need to access their internal state through their accessors. There are good reason for that but that will be for another time
</details>

## 132. What is a Component?
<details>
  <summary>Short Answer</summary>

Field of a record
</details>
<details>
  <summary>Less Short Answer</summary>

This definition is very precise, the elements you defined along with your record definition are called `Record Components`. The component word became a Java notion when Record were added to the language. In the reflection API for instance you have a method `getRecordComponents()` on the `Class.class` or when you create an annotation you can state that it can be added on a record component and for that the element type Enumeration that defines all the elements on which you can add an annotation has a value record component.

```java
java.lang.annotation.ElementType.RECORD_COMPONENT;
```

One last word, when you declare a record component, the compiler gives you an accessor for it. It uses it to create an `equals()` and `hashCode()` method as well as a `toString()` method all that for free. Neat!
</details>

## 133. What are the main operations of a Stack or a Queue?
<details>
  <summary>Short Answer</summary>

`peek`, `pop`, `push`
</details>
<details>
  <summary>Less Short Answer</summary>

These 2 data structures are the two simplest data structures you can imagine. `Peek` allows you to check the next available element without removing it. You cannot see the other elements. `Pop` removes it, now you have it and you can do something with it. `Push` adds an element. If it's a Stack then pick will show you the last element that was pushed and if it's a Queue then peek shows you the first element that was pushed maybe some time ago.

```java
interface Queue<E> { }
interface Deque<E> {
  //...
  E peek();
  E pop();
  void push(E e);
}
```

One last word, there are two interfaces to model these `Queue` and `Deque` which stands for `Double Ended Queue` and a number of implementations like a `ArrayDeque` for instance or `ConcurrentLinkedQueue` which is thread safe
</details>

## 134. What is an Entry and how can you create one?
<details>
  <summary>Short Answer</summary>

It is a key value pair in a Map
</details>
<details>
  <summary>Less Short Answer</summary>

This key value pair is modeled by the `Map.Entry` interface. From it, you can read and update the value and you can read the key but you cannot modify it. The easiest way to create a key value pair is to use the `Map.Entry` factory method from the Map interface. It gives you an unmodifiable entry. You can create an unmodifiable map from entries with the `Map.ofEntries()` factory method, be careful because none of these factory methods accept null keys or null values.

```java
Map.Entry<Integer, String> e1 = Map.entry(1, "one");
Map.Entry<Integer, String> e2 = Map.entry(2, "two");

Map<Integer, String> map = Map.ofEntries(e1, e2);
Set<Map.Entry<Integer, String>> set = map.entrySet();
```

One last word, you can also get a Set of the entries of a map with the `map.entrySet()` method. This set has very specific properties but that will be for another time
</details>

## 135. What type of ExecutiveService can you cite?
<details>
  <summary>Short Answer</summary>

`newSingleThreadExecutor()` that creates only one thread in the pool
</details>
<details>
  <summary>Less Short Answer</summary>

This question refers to the factory methods of the `Executors.class`. There are some that you probably need to know `newFixedThreadPool()` and you can pass the number of threads that you want. `newCachedThreadPool() that creates threads on demand can reuse use them but that will let them die after 60 seconds. Some of these factory methods also take a thread factory as an argument that you can use to generate the name of the thread for instance or to decide if they are daemon threads or not.

```java
// a pool with 1 thread
var exec1 = Executors.newSingleThreadExecutor();
// a pool with 5 threads
var exec2 = Executors.newFixedThreadPool(5);
// a pool that let threads die
var exec3 = Executors.newCachedThreadPool();

var factory1 = Thread.ofVirtual().factory();
var factory2 = Thread.ofVirtual().name("custom name").factory();
var factory3 = Thread.ofPlatform().name("custom name").daemon(true).factory();
```

One last word, with the JDK21 you even have a `newVirtualThreadPerTaskExecutor()` that create virtual threads on demand and let them die at the end
</details>

## 136. What is a defensive copy?
<details>
  <summary>Short Answer</summary>

A pattern by which you create a copy of an object when you receive it or when you return it
</details>
<details>
  <summary>Less Short Answer</summary>

It is useful when this object is modifiable like an ArrayList, a HashMap or a plain array for instance. If you don't do this copy someone with a reference to this object will be able to modify it and thus modify the internal state of your object. in a record for instance, if you have an array as a component you need to copy it both in the constructor to make sure that no one has a reference on it and in the accessor for the same reason.

```java
record Country(City[] cities) {
  Country(City[] cities) {
    this.cities = Arrays.copyOf(cities);
  }
  City[] cities() {
      return Arrays.copyOf(cities);
  }
}
```

One last word, you don't need a defensive copy with unmodifiable objects but be careful you need to make sure that they do not have any reference to other modifiable objects
</details>

## 137. What is a for-each loop?
<details>
  <summary>Short Answer</summary>

a syntaxic sugar to iterate over an Iterable
</details>
<details>
  <summary>Less Short Answer</summary>

This syntax works for any iterable that includes all the Collections and the Arrays. Internally the compiler creates an iterator for you and use it to traverse your iterable. You may be thinking that this extra object is an overhead but it can quickly be removed by the JVM through its escape analysis optimization. No one can get a reference to this iterator so in the end the JVM may decide to drop it.

```java
var list = List.of(...);
for(var city: list) {
    //...
}
```

One last word, if what you have is an iterable, you can also use its `forEach()` method and pass your Consumer to it. This forEach method uses a for-each loop internally so it will not make your code any faster but it can make it easier to read

```java
interface Iterable<T> {
  //...
  default void forEach(Consumer<? super T> action) {
    Objects.requireNonNull(action);
    for (T t : this) {
      action.accept(t);
    }
  }
}
```
</details>

## 138. What is the difference between an Enumeration and an Iterator?
<details>
  <summary>Short Answer</summary>

An Enumeration is something you should not be using anymore
</details>
<details>
  <summary>Less Short Answer</summary>

Back in the days a long time ago before the Collections framework was added to the JDK in 1998 that was Java 2, the Enumeration interface was the interface you had to use to iterate over the elements of a Vector, now you have the Collection framework, no reason to use Vector anymore. You can use ArrayList instead or a concurrent collection from `java.util.concurrent` if you need thread safety.

```java
class ArrayList<E> {
    ...
    Iterator<E> iterator() {
        ...
    }
}
```

One last word, as the Java doc says the functionality of this interface is duplicated by the Iterator interface and if you see one, you can call it asIterator() method to use it as an Iterator
</details>

## 139. What is the Diamond Problem in object-oriented programming?
<details>
  <summary>Short Answer</summary>

Something that default methods in interfaces brought to the Java platform
</details>
<details>
  <summary>Less Short Answer</summary>

These problem comes with multiple inheritance of behavior. Before Java 8, Java used to support only the inheritance of type. Class can implement several interfaces. Starting with Java 8, you can have default methods that is behavior in interfaces so if a given class implements two different interfaces that happen to have the exact same default method but are doing two different things then what you have is a diamond problem.

```java
interface A {
  default void m(){
    // ...
  }
}
interface B {
  default void m(){
    // ...
  }
}
class C implements A, B {
  // diamond problem doesn't compile
  @Override
  public void m() {
    //A.super.m();
  }
}
```

One last word, how can you fix that, well the good news is that the compiler can see this problem and will ask you which default method you want to call at compile time
</details>

## 140. What is a compact constructor?
<details>
  <summary>Short Answer</summary>

A syntax that you can use to write the canonical constructor of records in a much simpler way
</details>
<details>
  <summary>Less Short Answer</summary>

The canonical constructor of a record is simply the constructor that takes all its components. You can have other constructors but they need to call this one. You can write this constructor in a compact form where you do not declare its parameters and you don't need to assign the arguments to the fields of your records. It gives you a very clean syntax especially when all you have to do is validate the arguments that you get but you can also do some defensive copy in a compact constructor if this is what you need.

```java
record User(String name) {
  User(String name) {
    this.name = Objects.requireNonNull(name);
  }

  User {
    name = Objects.requireNonNull(name);
  }
}

record Country(City[] cities) {
  Country {
    cities = Arrays.copyOf(cities);
  }
}
```

One last word, records are really great to improve the readability and expressiveness of your code. You can create them on the fly as local records so you should definitely use them everywhere you can
</details>

## 141. What is a Deque?
<details>
  <summary>Short Answer</summary>

A double-ended queue
</details>
<details>
  <summary>Less Short Answer</summary>

There are two interfaces that you should use when you need a Queue or a Stack in Java. Queue and Deque that extends Queue. You can peek, pop or push by both ends of a Deque and it makes it a model for both Stacks and Queues. In Java, Deque defines the two behavior you need when you want to push an item in a full queue or to pop one from an empty queue and these two behaviors are immediately fail with an exception or immediately return true or false if the operation succeeded or failed.

```java
interface Queue<E> {}
interface Deque<E> extends Queue<E> {
    // insert HEAD
    // throws an exception
    void addFirst(E e);
    // immediately returns false
    boolean offerFirst(E e);
    
    // remove HEAD
    // throws an exception
    E removeFirst(E e);
    // immediately returns null
    E pollFirst(E e);
}
```

One last word, deque has an extension; `BlockingDeque` that models concurrency. It adds a third behavior, instead of reacting immediately it can block until your push or your pop can succeed
</details>

## 142. What is a Deep Copy?
<details>
  <summary>Short Answer</summary>

A mechanism to copy an object on all its related objects
</details>
<details>
  <summary>Less Short Answer</summary>

There are 2 ways to duplicate objects Deep copy and Shallow copy. Shallow copy just copies the current object. If this object is referencing more objects, they are not copied. Deep copy visits all the graph of the reference objects and copies them which can be costly because it is hard to know in advance what is the cost of a deep copy, shallow copy is usually the default behavior.

```java
List<E> copyOf(Collection<E> col) {
    if (col /* is non-modifiable*/) {
        return (List<E>)col;
    }
}
```

One last word, if your objects are non-modifiable then there is no need to copy them. You can check the source code of `List.copyOf()` for instance, it first checks if the list is non-modifiable and in that case just returns it
</details>

## 143. What is a ForkJoinPool?
<details>
  <summary>Short Answer</summary>

A pool of threads used for Parallel Streams
</details>
<details>
  <summary>Less Short Answer</summary>

This pool of threads is called the Common Fork-Join Pool and there is only one in your JVM. It is created when your JVM starts and waits for your parallel streams to use it. The ForkJoinPool is named after the algorithm used in parallel streams. First, you split your data set again and again until it chunk you have is small enough to be processed in a reasonable amount of time. That's the Fork phase and then you merge everything to compute the final result that's the Join phase.

One last word, you should be careful with parallel streams, they may be much more costly than what you think. One piece of advice, if you're writing a service bound to run in an application server you should stay away from them
</details>

## 144. What is an EntrySet?
<details>
  <summary>Short Answer</summary>

A Set that contains the key/value pairs of a Map
</details>
<details>
  <summary>Less Short Answer</summary>

You can call `map.entrySet()` to get this Set. It is a Set of `Map.Entry`, the interface that models your key value pairs. This set is actually a view on your map. You cannot add anything to it if you try to do that you will get an exception but you can remove elements from it either directly or through an iterator, doing that remove the corresponding key/value pair from your map.

```java
interface Map<K, V> {
  Set<Map.Entry<K, V>> entrySet();
}

var entries = map.entrySet();
// clears the map
entries.clear()

for (var iterator = map.entrySet(); iterator.hasNext();) {
  var entry = iterator.next();
  if (entry.getKey() % 2 == 0) {
      iterator.remove();
  }
}
```

One last word, if your map is a `SequencedMap` instead of Map then you can call sequenced EntrySet() on it to get a sequence set instead of a regular set
</details>

## 145. What does fall-through mean?
<details>
  <summary>Short Answer</summary>

With no doubt trouble!
</details>
<details>
  <summary>Less Short Answer</summary>

This is something that can happen if you're using switch in your application, unfortunately you don't so there is very little chance that you can see this problem. In case you do the problem is the following suppose you switch on an Enum for instance but forgot to add a break after each label then your code will carry on with the next one which is usually not what you want.

```java
enum Day {
    Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday
}
void main(Day value) {
  switch (value) {
    case Monday, Tuesday, Thursday, Friday -> System.out.println("School");
    case Wednesday, Saturday, Sunday -> System.out.println("Rest"); 
  }
  // > value = Day.Tuesday
  // School
  // Rest
}
void mainWithBreak(Day value) {
  switch (value) {
    case Monday, Tuesday, Thursday, Friday -> System.out.println("School"); break;
    case Wednesday, Saturday, Sunday -> System.out.println("Rest");
  }
  // > value = Day.Tuesday
  // School
}
```

One last word, maybe you will be using switch expressions and statements more and more in the future because it is now part of the Data-Oriented Programming paradigm currently being added to the Java language but that will be for another time
</details>

## 146. What is a Collectors.toMap()?
<details>
  <summary>Short Answer</summary>

A collector to create Maps
</details>
<details>
  <summary>Less Short Answer</summary>

Collectors are objects, you can pass to the `collect()` method of the Stream API. `Collectors.toMap()` takes 2 functions both are applied to the element of your streams. The first one is used to compute the key and the second one to compute the value. In case 2 elements produce the same key then you need to provide a merge function if you don't you will get an exception at runtime. You can also provide a Supplier that will be used to create your empty map useful to create TreeMaps for instance.

```java
Map<Integer, String> map = Stream.of("1", "11", "22", "111")
        .collect(Collectors.toMap(
                s -> s.length(),
                s -> s,
                (s1, s2) -> s1 + s2),
                TreeMap::new
        );
        //.collect(Collectors.groupingBy(s -> s.length()))
```

One last word, you also have the `groupingBy()` collector which adds the element that produce the same key to the same list. Neat.
</details>

## 147. What is a Lock?
<details>
  <summary>Short Answer</summary>

An interface
</details>
<details>
  <summary>Less Short Answer</summary>

It is used to model the object you can use to ensure that only one thread can execute a piece of code at a given time. There are several ways to do that in Java. The first one is the `Synchronized Block`. It has always been there and the second one is the `Lock` interface implemented by the `ReentrantLock` class added in Java 5. The pattern to use this object is to create it then call lock() then use it and release it in a try-finally block to make sure that in case something goes wrong your lock will always be unlocked.

```java
Lock lock = new ReentrantLock();
lock.lock();
//lock.tryLock(1, TimeUnit.SECONDS);
try {
  // only one thread can execute this  
} finally {
    lock.unlock();
}
```

One last word, you can do many more things with locks than with synchronized blocks like trying to lock but with the timeout for instance
</details>

## 148. How can you create a Collection from an Iterable?
<details>
  <summary>Short Answer</summary>

Why would you do that? Are you sure that this is what you need?
</details>
<details>
  <summary>Less Short Answer</summary>

And iterable is something that can produce elements without having to store them in memory all at once so you can process many elements with this pattern with a small memory footprint for instance you can create a stream from this iterable and unless you go distinct() or sorted() on your stream, it will not store anything in your memory so if you are really really sure that this is what you need then here is the pattern.

```java
Iterable<String> iterable = ...;

// process with a stream
Streams.stream(iterable)
    .map(...)
    .filter(...)
    .collect(...)

// are you REALLY REALLY sure?
var list = Streams.stream(iterable).toList();
```

One last word, loading your data in memory can dramatically increase your memory footprint so make sure you need it before doing it
</details>

## 149. What is the filter() method?
<details>
  <summary>Short Answer</summary>

A method to prevent elements from a stream to be passed to the next stage of your pipeline
</details>
<details>
  <summary>Less Short Answer</summary>

A filter() method does not really remove elements from a stream because a stream is an empty object. There is no element in a stream. A stream consumes element from a source, process them one stage at a time and then reduces them. The filter operation takes a predicate as a parameter that decides if a given element can be passed or not.

```java
var ints = Stream.of(1, 2, 3, 4, 5, 6)
        .filter(i -> i % 2 == 0)
        .toList();
System.out.println(ints);
// > [2, 4, 6]
```

One last word, you can also filter using two other operations, `mapMulti()` and `flatMap()` which may be useful if you cannot express your validation as a simple predicate but that will be for another time
</details>

## 150. How is QuickSort working?
<details>
  <summary>Short Answer</summary>

Quickly!
</details>
<details>
  <summary>Less Short Answer</summary>

The first step consists in choosing a pivot. Your best choice is to choose a value that will split your set into two equal parts then you compare all the elements to the pivot, the lesser elements go to the left, the greater to the right and then you rinse and repeat on the two halves of your set again and again and until you have intervals of size 2.

```
8 1 1 2 3 8 7 5 9 5 6 5 6 4 7 4
1 1 2 3 5 5 4 4 5 8 7 8 9 6 6 7
1 1 2 3 5 5 4 4 5 6 6 7 7 8 8 9
1 1 2 3 4 4 5 5 5 6 6 7 7 8 8 9
(# comparisons per step) = N
pivot = 5
```

One last word, How many operations do you need? Well each step consist in N comparison and you divide your set in 2, again and again, until you cannot do it anymore so the number of steps is such that N divided by two power(2^) the number of steps is still greater than one that's n log of n `nlog(n)` you knew that already now you sure
</details>

## 151. What is a Text Block?
<details>
  <summary>Short Answer</summary>

A syntax to write strings of characters
</details>
<details>
  <summary>Less Short Answer</summary>

You open a text block with a triple double quote `"""` followed by a line terminator. Then all the text that follows in your source code is part of the string you're creating until you put another triple double quote that closes your string. A text block usually spans over several lines of your source code, you can add any kind of character in a text block without having to escape them. The blank characters at the beginning of each line are not part of your text they are called `incidental white spaces`.

```java
var textBlock = """
        This is a block of text
        With a second line
        And some <code>"HTML"</code>
        And some blanks at the end  \s
        """;
```

One last word, you can control the start and the end of each line by adding a `\s` character. Text blocks are great you should use them wherever you can
</details>

## 152. How can you loop backward?
<details>
  <summary>Short Answer</summary>

There is a method for that
</details>
<details>
  <summary>Less Short Answer</summary>

It only works if your collection is ordered, meaning that it is in fact a List. Most of the time it is the case because ArrayList is your favorite implementation. There is a `listIterator()` method on List that does not exist on collection and that returns the `ListIterator`. ListIterator extends Iterator so you have the classic called `next()` and `hasNext()` but you also have `previous()` and `hasPrevious()` to iterate backward.

```java
interface List<E> {
  Iterator<E> iterator();
  ListIterator<E> listIterator();
}
interface ListIterator<E> extends Iterator<E> {
  E next();
  boolean hasNext();
  
  E previous();
  boolean hasPrevious();
  
  int nextIndex();
  int previousIndex();
  
  void set(E e);
  void add(E e);
}
```

One last word, you also have a `nextIndex()` and `previousIndex()` methods as well as `set()` an `add()` to set the current element and insert an element through this ListIterator, all this is supported by the ArrayList implementation
</details>

## 153. What is a Semaphore?
<details>
  <summary>Short Answer</summary>

A Lock with several permits
</details>
<details>
  <summary>Less Short Answer</summary>

A classical Lock can give access to the block of code it protects to only one thread at a time. A semaphore can give access to several threads. You can create a semaphore by giving it to number of permits then you can use it to protect a block of code. A thread needs a permit to execute the protector code and if there is none available then it blocks until there is one. Don't forget to release your permit in a finally block. Semaphore are useful when you need to limit the number of threads that can access an external resource.

```java
var semaphore = new Semaphore(4);
semaphore.acquire();
try {
    // your code
} finally {
    semaphore.release();
}
```

One last word, Semaphores can also be fair, meaning that the first thread that was blocked is the first one to be given a permit
</details>

## 154. What is the MethodHandle?
<details>
  <summary>Short Answer</summary>

An object to access the members of an object using Reflection
</details>
<details>
  <summary>Less Short Answer</summary>

There is a caveat in using the Reflection API with the field or method objects. It needs to check access on each invocation and this is quite slow. a MethodHandle is a reference to an existing member of a class but the checks are made when you create the MethodHandle, you can invoke public constructors by getting a reference to it with the `findConstructor()` method, same for public methods with the `findVirtual()` method or public fields with `findGetter()` and `findSetter()`.

```java
class User {
  String name;
  User(String name) {...}
  String name() {...}
}
var lookup = MethodHandles.Lookup();

// findConstructor
var constructorMH = lookup.findConstructor(User.class, MethodType.methodType(void.class, String.class));
var maria = (User)constructorMH.invokeExact("Maria");

//findVirtual
var getterMH = lookup.findVirtual(User.class, "name", MethodType.methodType(String.class));
var name = (String)getterMH.invokeExact(maria);

//findGetter
var fieldReadMH = lookup.findGetter(User.class, "name", MethodType.methodType(String.class));
var name = (String)fieldReadMH.invokeExact(maria);

//findSetter
var fieldWriteMH = lookup.findSetter(User.class, "name", MethodType.methodType(String.class));
var name = (String)fieldWriteMH.invokeExact(maria, "MARIA");
```

One last word, MethodHandles do not give you access to private members from outside of a class for that you need to use the classical Field or Method classes
</details>

## 155. Why should you prefer private fields and accessors?
<details>
  <summary>Short Answer</summary>

Because it is safer
</details>
<details>
  <summary>Less Short Answer</summary>

A private field must be accessed through an accessor, meaning that you can control the access and there are 2 things that you can easily do. The first one is the defensive copy, sometimes you need to protect your internal state from outside modifications even if your field is final it can be a reference to a mutable container that you need to copy when you build your object. And the second one is concurrent access. Fields can be declared `volatile` but it only makes the reference thread safe. You can then guarantee thread-safety using a synchronized block.

```java
public class User {
  private int[] labels;

  User(int[] labels) {
    this.labels = Arrays.copyOf(labels);
  }

  public int labels() {
    return Arrays.compare(labels);
  }
}
```

One last word, by default always use private fields. Always!
</details>

## 156. What is the difference between an Interface and an Abstract Class?
<details>
  <summary>Short Answer</summary>

Well, it's not the same thing.
</details>
<details>
  <summary>Less Short Answer</summary>

There are 2 major differences; First, an Abstract Class has a constructor which is called to construct your final object, it is not the case for an interface and second, an Abstract Class can carry a mutable state which is again not the case for an Interface. This question may sound like a trick question because you can have static and instance method in both abstract classes and interfaces, it is a feature that was added in Java 8 in 2014.

```
Abstract class:
  - constructor
  - mutable state
Interface:
  - no constructor
  - does not carry any state
```

One last word, now you may be wondering when should one use abstract classes or interfaces. By default, prefer interfaces. Why?, well that will be for another time
</details>

## 157. How can you create a directory with Java I/O?
<details>
  <summary>Short Answer</summary>

There is a method for that.
</details>
<details>
  <summary>Less Short Answer</summary>

The method is called `createDirectory()`. It is a factory method from the `Files.class` and it takes a Path as a parameter so the pattern is very simple, call `createDirectory()` pass a Path and you're done. You can also pass file attributes that can set the permission you want to set for this directory here is a classical example for a public directory.

```java
Path dir = Path.of("new-dir");
var createdDir = Files.createDirectory(dir);

// permissions
var fileAttributes = PosixFilePermissions.asFileAttribute(PosixFilePermissions.fromString("rwxr-xr-x"));
Path dir = Path.of("new-dir");
var createdDir = Files.createDirectory(dir, fileAttributes);
```

One last word, there is also a `Files.newDirectories()` method that takes the same parameters but that can create any intermediate directory on the path to the directory you want to create. Neat.
</details>

## 158. How is the `map.values()` method working?
<details>
  <summary>Short Answer</summary>

`map.values()` is a mutable view on the values of a Map
</details>
<details>
  <summary>Less Short Answer</summary>

`map.values()` return returns a collection of the values present in your map and this collection is a view on the content of your map that reflects its modifications. This view is also mutable, it supports `remove()` from the collection itself and from an Iterator; `removeAll()` and `retainAll()`. It does not support the addition of new elements and removing a value removes the corresponding key value pair.

```java
Map<K, V> map = ...;

// OK
Collection<V> values = map.values();
var iterator = values.iterator();
iterator.remove();
values.remove(otherValue);
values.removeAll();
values.retainAll(someCollection);
values.clear();

// NOT OK
values.add(...);
```

One last word, if a value is present several times in your map then one of them is removed. It is the first that is found when your implementation iterates over them but it may not be the first that you added to your map.

```java
public static void main(String[] args) {
    // Create a map with duplicate values
    Map<String, Integer> map = new HashMap<>();
    map.put("A", 1);
    map.put("B", 2);
    map.put("C", 3);
    map.put("D", 2); // already added
    map.put("E", 4);

    System.out.println("Original Map: " + map);
    // Original Map: {A=1, B=2, C=3, D=2, E=4}

    // Value to be removed
    int valueToRemove = 2;

    // Remove one occurrence of the value
    Iterator<Map.Entry<String, Integer>> iterator = map.entrySet().iterator();
    while (iterator.hasNext()) {
        Map.Entry<String, Integer> entry = iterator.next();
        if (entry.getValue().equals(valueToRemove)) {
            iterator.remove();
            break; // Remove only one occurrence
        }
    }

    System.out.println("Modified Map: " + map);
    // Modified Map: {A=1, C=3, D=2, E=4}
}
```
</details>

## 159. What is the first thing that the constructor does?
<details>
  <summary>Short Answer</summary>

It calls another constructor
</details>
<details>
  <summary>Less Short Answer</summary>

This constructor can be a constructor from the same class called by `this()` or from a super class called by `super()`. If you don't write any such call explicitly, then the compiler will add one for you. This series of super() calls lands in the Object class. In the case of Records any constructor other than the canonical constructor must call another constructor. In the end this chain of calls must call the canonical constructor.

```java
class User {
    User(String name, int age) {
        super(); // compiler
    }
    User(String name) {
        this(name, 30);
    }
}
```

One last word, you cannot add any instruction before this call to this() or super(). Being able to execute code before this call is actually being discussed and should become a feature, we will talk more about this later
</details>

## 160. How can you create a Stream from an Iterator?
<details>
  <summary>Short Answer</summary>

There is a code pattern for that
</details>
<details>
  <summary>Less Short Answer</summary>

First, you need to create a spliterator from your iterator using the Spliterator factory class and then you need to pass the Spliterator to the StreamSupport factory class. The `Spliterator.UnknownSize()` factory method also take the Characteristics of the Spliterator you want to create. There are several that you can choose from DISTINCT, NONNULL, SORTED for instance. To build your stream you need to tell the API if you're going to use it in parallel or not.

```java
Iterator<String> iterator = ...;
var spliterator = Spliterators.spliteratorUnknownSize(iterator, Spliterator.DISTINCT, Spliterator.NONNULL, Spliterator.SORTED);

var stream = StreamSupport.stream(
        spliterator,
        false // not parallel
);
```

One last word, these Spliterator Characteristics are a very interesting feature of the API that can greatly speed up your stream computations but that will be for another time
</details>

## 161. Why should you not use static initializers?
<details>
  <summary>Short Answer</summary>

Because you can't prevent this code to run
</details>
<details>
  <summary>Less Short Answer</summary>

You can run your application in two context at least; in production and to run your test. Odds are that your production context is not the same as your test context. Suppose you create a logger that logs to a file or database then you need the same file system or the same database. You can play with the configuration files for that but then what you do is not return in your code anymore using dependency injection for instance leads to a code that is much easier to understand.

```java
class User {
  static Logger logger = Logger.getLogger(User.class);
}
// or
class User {
    Logger logger;
    User(Logger logger) {
      this.logger = logger;
    }
}
```

One last word, there are some examples of static initializers in a JDK itself but that's okay because that's the same JDK, whether you're using it to test your application or to run it in a production environment
</details>

## 162. What is a ReadWriteLock?
<details>
  <summary>Short Answer</summary>

A lock that enables parallel reads and blocks on writes
</details>
<details>
  <summary>Less Short Answer</summary>

Locks are used to prevent race conditions. Race Condition occurs when two threads are writing and reading the same field. Will thread B see the value written by thread A? Synchronization achieves that by blocking everything, ReadWriteLock works with 2 locks; one for the read operations and another one for the write operations. The write lock is exclusive, no other lock can be taken when it is active. The read lock on the other hand is not, you can have any number of active read blocks.

```java
ReadWriteLock lock = new ReentrantReadWriteLock();

void read() {
    var readLock = lock.readLock();
    readLock.lock();
    try {
        // as many thread as needed
        // no write, as many reads
    } finally {
        readLock.unlock();
    }
}
void write() {
  var writeLock = lock.writeLock();
  writeLock.lock();
  try {
    // one thread
    // no other write
  } finally {
    writeLock.unlock();
  }
}
```

One last word, of course this is an optimization only if your number of write operations is much smaller than the number of read operations
</details>

## 163. What is the difference between an Iterator and a Spliterator?
<details>
  <summary>Short Answer</summary>

An Iterator is used by Collections, a Spliterator is used by Streams
</details>
<details>
  <summary>Less Short Answer</summary>

Spliterator comes from the contraction of Iterator and split which means that you can split the data and Iterator it's pulling its data from a source. a Spliterator on the other hand sends a consumer with its `tryAdvance()` method and let this source called this consumer. And if there is no more element this tryAdvance() method should return false so Spliterator works on a push model.

```java
interface Spliterator<E> {
    boolean tryAdvance(Consumer<E> consumer);
}
```

One last word, you can actually implement your own Spliterator to create operations on streams like shifting, sliding, zipping or even folding. It's a little tricky but doable
</details>

## 164. How is the `Map.keySet()` method working?
<details>
  <summary>Short Answer</summary>

`Map.keySet()` is a mutable view on the keys of a Map
</details>
<details>
  <summary>Less Short Answer</summary>

`Map.keySet()` is a set of the keys of your map, you can't have duplicates among your keys so that's a set. This view is mutable but not all operations are supported in it. You can delete keys from this set with `remove()`, `removeIf()`, `removeAll()`, `clear()` and `retainAll() and you can also delete element through its iterator but you cannot add elements to it. If you try to do that you will get an UnsupportedOperationException.

```java
Map<Integer, String> map = Map.of(1, "one", 2, "two", 3, "three");
Set<Integer> keySet = map.keySet();
keySet.add(4); // Exception in thread "main" java.lang.UnsupportedOperationException
```

One last word, do not use this Set if what you need is to iterate over the key-value pair of your map because it's inefficient, you have another set for that you can get with `Map.entrySet()`
</details>

## 165. What is a Garbage Collector?
<details>
  <summary>Short Answer</summary>

A wonderful piece of technology that does incredible things for you!
</details>
<details>
  <summary>Less Short Answer</summary>

A Garbage Collector is an element of the Java Virtual Machine that works under the hood and takes care of your memory for you. There are actually several garbage collectors available which you can choose from, you can decide which one you want to use when you launch your application. It is the responsibility of your garbage collector to give you the memory you need to create your objects and to reclaim this memory when you are not using it anymore.

```
Garbage Collector
- One is active at a time
- Several to choose from
- Gives you memory
- Reclaims it
```

One last word, garbage collectors are actually critical to get good performance for your application and they are a lot of investment in this piece of technology. The 2 last one `ZGC` and `Generational ZGC` are doing wonders but that will be for another time
</details>

## 166. What is a Final Class?
<details>
  <summary>Short Answer</summary>

A class that you cannot extend.
</details>
<details>
  <summary>Less Short Answer</summary>

Final is a keyword that you can add on many elements of your source code. If you add it on the declaration of your class and someone tries to extend this class then the compiler will generate an error. There are elements that you can create in Java that are compiled as final classes this is the case for `Enums` compiled as a final class that extends `java.lang.Enum` and the case for Records also compiled as a final class that extends `java.lang.Record`

```java
final class CannotBeExtended {}

// compiled as a final class that extends java.lang.Record
record Point(int x, int y) {}
```

One last word, instead of forbidding the extension of your class, you can also control it by making it `sealed` and publishing the list of classes that can extend it. It works really well especially in conjunction with the switch on types but that will be for another time
</details>

## 167. How can you join the elements of a Collection of Strings?
<details>
  <summary>Short Answer</summary>

There is a method for that.
</details>
<details>
  <summary>Less Short Answer</summary>

You can use the `join()` method of the String class that takes a delimiter and an Iterable. It can also take a vararg if you don't need the delimiter, you can still pass an empty string to this method call. You should really use this pattern because it has been carefully optimized to make sure that it is as fast as possible and much faster than any StringBuilder based pattern that you may be using. You can check the source code to get a hint at it.

```java
var joined = String.join("one", "two", "three");
System.out.println(joined);
// > one two three

var strings = List.of("one", "two", "three");
var joiner = new StringJoiner(" ", "{", "}");
string.forEach(joinder::add);
System.out.println(joinder);
// > {one two three}

var ints = List.of(1, 2, 3);
var joined = ints.stream()
        .map(Object::toString)
        .collect(Collectors.joining(" "));
System.out.println(joined);
// > 1 2 3
```

One last word, there are other patterns that you may want to check. One is based on the use of the StringJoiner class that can take a prefix and a suffix, as well as the `Collectors.joining()` collector which can be useful if you need to map your elements before joining them
</details>

## 168. What does volatile mean?
<details>
  <summary>Short Answer</summary>

It has to do with concurrency and race conditions
</details>
<details>
  <summary>Less Short Answer</summary>

Volatile is a keyword you can use when declaring a field and you should use it when there is a possibility of race condition on this field that is several threads can read and modify this field. Declaring a field volatile ensures that a thread reads the last value that was return to this field even if this write occurred in another thread. The exact rule is the following a synchronized or volatile read always returns the last value written by a synchronized or volatile write.

```java
class User {
    volatile String name;
    void upperCase() {
        name = name.toUpperCase();
    }
    String name() {
        return this.name;
    }
}
```

One last word, this definition is actually the definition of the happens-before link between read and write operations but that will be for another time
</details>

## 169. How can you generate random numbers?
<details>
  <summary>Short Answer</summary>

There is an interface for that.
</details>
<details>
  <summary>Less Short Answer</summary>

If what you need is just a simple series of random numbers, you can use the `java.util.Random` class. Starting with the JDK 17, random generators implement the Random Generator interface that models what a random generator can do. Basically, you can generate series of any primitive types, evenly distributed or that follow a Gaussian distribution: You can ask for one element at a time with the `nextXXX()` methods or you can generate streams.

```java
import java.util.random.RandomGenerator;

var random = new Random(314L);
var d = random.nextDouble();
var i10 = random.nextInt(0, 10);
LongStream stream = random.longs();

String algorithm =
// L32X64MixRandom
// L64X128StarStarRandom
// L64X128MixRandom
// L64X256MixRandom
// L64X1024MixRandom
// L128X128MixRandom
// L128X256MixRandom
// L128X1024MixRandom
// Xoroshiro128PlusPlus
// Xoroshiro
// Xoshiro256PlusPlus
var random = RandomGenerator.of(algorithm);
```

One last word, if you are working in cryptography or if you need a specific random number generator then you need to check the documentation of the `java.util.random` page that gives you all the detail of the algorithms available in the JDK.
</details>

## 170. What is a Supplier?
<details>
  <summary>Short Answer</summary>

A functional interface
</details>
<details>
  <summary>Less Short Answer</summary>

The Supplier interface models lambdas that do not take any parameter and return something. These lambdas are very useful when you need to model the construction of an object. Suppose that you need to log a message or to throw an exception but this message or this exception is expensive to create. If you pass this argument then it will be created when you call your method even if this method decides not to use it. This can be the case if your log level is not the right one or if there is no need to throw this exception, in that case you can pass a supplier that can create this message or this exception. If the method needs to create it then it can call the get method of this supplier.

```java
@FunctionalInterface
public interface Supplier<T> {
    T get();
}

Supplier<MyAppException> supplier = () -> new MyAppException();
// it could be empty
Optional<String> optional = ...;
var value = optional.orElseThrow(supplier);

class Optional<T> {
  Throwable orElseThrow(Supplier<Exception> supplier) {
      if (isPresent()) {
          return this.value;
      } else {
          throw supplier.get();
      }
  }
}
```

One last word, suppliers are very useful, you should use them wherever you can
</details>

## 171. How can you join the elements of a Stream of Strings?
<details>
  <summary>Short Answer</summary>

There is a Collector for that.
</details>
<details>
  <summary>Less Short Answer</summary>

You can call `collect()` on your stream and pass the `Collectors.joining()` collector to this method. This joining() factory method has several overloads; the first one doesn't take any parameter and joins all the strings of your stream. The second one takes a separator that is inserted between each element and the third one takes a separator a prefix and a suffix and yes these last two handle empty streams or singletons properly.

```java
var ints = Stream.of("one", "two", "three");
ints.collect(Collectors.joining());
// > onetwothree

ints.collect(Collectors.joining(", "));
// > one, two, three

ints.collect(Collectors.joining(", ", "[", "]"));
// > [one, two, three]
```

One last word, be careful because this collector works only on Streams of Strings, if you pass it to a stream of objects for instance you will get a compiler error
</details>

## 172. What does transient mean?
<details>
  <summary>Short Answer</summary>

It is used to prevent a field to be serialized.
</details>
<details>
  <summary>Less Short Answer</summary>

Serialization consists in saving a root object along with all the graph of objects it points to, to a binary stream that can be saved to a file or send to the network. You can then recreate all this graph on another machine. Sometimes your object has references to elements that are sensitive or system dependent like files or network connections and you don't want these elements to be serialized, well that's where you can use the transient keyword. Add it on the field and this field will not be serialized.

```java
// You don't want to expose securityKey
class Message {
    String message;
    transient String securityKey;
}
```

One last word, serialization used to be a great idea when Java was created but it brings many issues including security issues so now you should stay away from that
</details>

## 173. How does the forEach() method work?
<details>
  <summary>Short Answer</summary>

It iterates over the elements of an iterable and pass them to a Consumer.
</details>
<details>
  <summary>Less Short Answer</summary>

There are actually 3 such methods; one on the Iterable interface and another one on the Stream interface that both take a Consumer and the third one on the Map interface that takes a BiConsumer. This method iterates over the elements of the iterable or the stream or over the key-value pairs of your map and passes them one by one to the consumer you pass as an argument. In the case of maps the BiConsumer accepts the key and the value of each of your key-value pairs.

```java
var map = Map.of(1, "one", 2, "two", 3, "three");
map.forEach((key, value) -> System.out.println(key + "::" + value));
/*
> 1::one
> 2::two
> 3::three
*/
```

One last word, apart from printing the content of a collection or a map, doing side effects in your Consumer is most of the time a bad idea. Try to use Streams instead of doing side effects
</details>

## 174. What is the difference between a Lock and a Semaphore?
<details>
  <summary>Short Answer</summary>

A Lock is an interface, a Semaphore is a class.
</details>
<details>
  <summary>Less Short Answer</summary>

Yes, but that's not the point. Locks and Semaphore are doing the same kind of things, locks can hold only one permit and the Semaphore for can hold as many as you need and it's still not the point, the biggest difference is that the lock may enforce that the thread that's releases the lock is the same as the thread that acquired it and it is the case for the ReentrantLock implementation, whilst the Semaphore explicitly states that the thread that releases a permit can be a different thread than the one that acquired it.

```java
var semaphore = new Semaphore();
semaphore.acquire();

// in some other thread
semaphore.release(); // also OK
```

One last word, this feature is very useful, it may allow you to unlock systems from the outside just by releasing permits from any other thread
</details>

## 175. What is the difference between Enum and Enumeration?
<details>
  <summary>Short Answer</summary>

Enumeration is an interface, Enum is a class. The only common elements between both is the first 4 letters of their name.
</details>
<details>
  <summary>Less Short Answer</summary>

Enumeration is an old stuff that you should not be using anymore. It's an interface that has been superseded by iterator when the collection framework was added to the JDK that was Java 2 1998. Enum is a great addition of the JDK 5 that allows you to control the instances of a given class. If you have only one instance, it gives you a singleton and Enum's are the preferred pattern to create singleton.

```java
enum SomeDays {
    SATURDAY(4), SUNDAY(5);
    int hours;
    SomeDay(int hours) {
        this.hours = hours;
    }
    int hours() {
        return this.hours;
    }
}

// Obsolete interface
interface Enumaration<E> {
    // Some obsolete methods
    // The only useful method
    Iterator<E> asIterator();
    
}
```

One last word, Enums are great, they can have methods, states and even custom constructors. Enumerations well just forget about that
</details>

## 176. What is a preview feature?
<details>
  <summary>Short Answer</summary>

A way to test upcoming features of the JDK before they become final.
</details>
<details>
  <summary>Less Short Answer</summary>

It's not just about testing, it's also about providing feedback so if you spot a bug or think about an improvement then you can go to the mailing list and talk about it. We can even get answers from the people who actually wrote the feature. You can find the right mailing list in a JEP that describes the feature. Preview features need to be activated to be used so no risk of using them by accident, usually you will activate them in your IDE.

One last word, be aware that a preview feature may change before becoming final. It can even be dropped so avoid using them in your application unless you really know what you're doing
</details>

## 177. How can you reduce a Stream?
<details>
  <summary>Short Answer</summary>

There are several method for that.
</details>
<details>
  <summary>Less Short Answer</summary>

Reducing a stream means combining all the elements produced by the streams into one final element that can be of a different type. There are 3 `reduced()` methods on the stream interface and 2 `collect()` methods that are reducing in a mutable container. IntStream, LongStream and DoubleStream have only 2 `reduce()` and 1 `collect()` but they have a `sum()`, a `min()` and a `max()` and also a nifty summary `statistics()` method that does the max(), the min(), the count(), the average() all in one pass over your data.

One last word, some reduced methods return an optional and there is a very good reason for that but that will be for another time
</details>

## 178. How is HashSet working?
<details>
  <summary>Short Answer</summary>

It wraps a HashMap.
</details>
<details>
  <summary>Less Short Answer</summary>

HashSet needs to store objects that are different and refuse to add an object that it already contains. It uses an internal HashMap for that, it adds your object to this HashMap and put them as the keys of the map associated to a dumb value called `PRESENT` in a source code. One consequence is that you should absolutely not mutate the state of an object once you have added it to a HashSet if you do that your set will not work properly.

```java
class HashSet<E> {
  HashMap<E, Object> map;
  static final Object PRESENT;
  boolean add(E e) {
      return map.put(e, PRESENT);
  }
}
```

One last word, if you have a lot of objects to add to a Set, try to create it with the right size up front. There is a factory method for that.
</details>

## 179. What is JShell?
<details>
  <summary>Short Answer</summary>

A REPL.
</details>
<details>
  <summary>Less Short Answer</summary>

REPL stands for `R`ead `E`valuate `P`rint `L`oop. It's actually a command line tool that you can use to quickly write snippets of code and test them: You can launch it with the command JShell that can take a bunch of options by the way you can see them by typing `jshell` and then you can create variables, call methods, create records and experiment with any feature. You can even activate the preview feature in jshell so you can also experiment with them.

```shell
$ jshell
| Welcome to JShell -- Version 21
| For an introduction type: /help intro

jshell> record Message(String content){}
| Created record Message
jshell> var m = new Message("Hello")
m ==> Message[content=Hello]
jshell>
```

One last word, you can even write your Java code on several lines with jshell which is very handy to create complex records for instance

```shell
$ jshell
| Welcome to JShell -- Version 21
| For an introduction type: /help intro

jshell> record User(String name) {
 ...>   public User { 
 ...>     Objects.requireNonNull(name); 
 ...>   } 
 ...> }
 | created record User
 jshell> var mary = new User("Mary")
 mary ==> User[name=Mary]
 jshell>
```
</details>

## 180. What is the difference between Comparator and Comparable?
<details>
  <summary>Short Answer</summary>

A Comparator can compare two objects, a Comparable can compare itself to another objects.
</details>
<details>
  <summary>Less Short Answer</summary>

Both are interfaces. Comparable defines a method that receives another object from the same class so a comparable object can compare itself to some other object. Comparator is also an interface it defines a method that receives two objects of the same type, these objects can be both Comparable but a Comparator can implement a different comparison.

```java
interface Comparator<E> {
  int compare(E e1, E e2);
}
interface Comparable<E> {
  int compareTo(E other);
}
```

One last word, unless you really need it don't implement your comparators yourself. Check the Comparator interface, first there are plenty of methods; factory methods and default methods that you can use for that
</details>

## 181. What is the difference between the reduce() method and the collect() method?
<details>
  <summary>Short Answer</summary>

They don't work the same
</details>
<details>
  <summary>Less Short Answer</summary>

These methods are methods from the Stream API. reduce() consist in applying a reduction operation on the elements consumed by your Stream. This operation is modeled by a `BiFunction` that should be associative. collect() reduces your element in a mutable container. Typically, a collection or a map. Stream<T> has a method collect() that takes a Collector as a parameter, whereas specialized streams do not. That's for type reasons, there is no specialized collector.

```java
import java.util.ArrayList;
import java.util.stream.Collectors;

var ints = Stream.of(1, 2, 3, 4, 5);
var sum = ints.reduce(0, (i1, i2) -> i1 + i2);
// > 15
var sum = ints.collect(Collectors.toList());
// > [1, 2, 3, 4, 5]

var list = ints.collect(ArrayList::new);
//var list = ints.collect(ArrayList::add);
//var list = ints.collect(ArrayList::addAll);
```

One last word, some reduce() methods return an Optional, and sometimes the corresponding collectors does the same but not always. That's the case for the summarizing collectors but that will be for another time
</details>

## 182. What is the vararg?
<details>
  <summary>Short Answer</summary>

An Array
</details>
<details>
  <summary>Less Short Answer</summary>

A vararg is a feature of the language that allows you to pass zero or more elements to a method, you declare your method in that way with the 3 dots and then you can call it with any number of strings. There are 2 constraints with vararg; first, you can only use one vararg per method and second this vararg parameter should be the last of your parameters. No parameter is allowed after a vararg, your compiler will tell you that. In your method this vog is an array by the way you can also pass an array to a method that declares the vararg.

One last word, you can also use vararg with constructors and because you can pass an array you should still use a defensive copy with vararg
</details>

## 183. How should you close an I/O resource?
<details>
  <summary>Short Answer</summary>

You should call it `close()` method
</details>
<details>
  <summary>Less Short Answer</summary>

The only safe way that guarantees that this method is called in all circumstances is to open your I/O resources in a try with resources statement, in that way even if an exception is interrupting your normal process, your close() method is called when your program exits the try block.

```java
try (
    var writer = Files.newBufferedWriter(path);
    var printer = new PrinterWriter(writer);
) {
    ...
} catch(Exception e) {
    ...
}// closes printer then writer


interface AutoCloseable {
    void close() throws Exception;
}
```

One last word, you can use any object that implements AutoCloseable with a try with resources pattern and to implement this interface you just need to create a close() method so creating your own AutoCloseable object is actually very simple, you should definitely use these patterns in your applications
</details>

## 184. What is the difference between a Fork-Join Pool and an ExecutorService?
<details>
  <summary>Short Answer</summary>

ExecutorService is an interface, Fork-Join Pool is a class
</details>
<details>
  <summary>Less Short Answer</summary>

There are many implementations of ExecutorService and Fork-Join Pool is, by the way, one of them. There is one point worth mentioning, with CachedThreadPool and FixedThreadPool available from the `Executors` factory class, your task are stored in a single waitlist where the threads can take them. In a Fork-Join Pool, there is one waitlist per thread and the pool implements the work-stealing pattern so that the thread can steal a task from another waitlist in case its own is empty.

```java
var fixedES = Executors.newFixedThreadPool();
var cachedES = Executors.newCachedThreadPool();
```

One last word, as of now, there are two Fork-Join Pools used by the JVM. One to run your parallel streams and another one to run your virtual threads
</details>

## 185. What is a Spliterator?
<details>
  <summary>Short Answer</summary>

An interface
</details>
<details>
  <summary>Less Short Answer</summary>

This interface models the way you can connect a stream to a source of data. The name comes from `Iterator` and `split` which is a feature used by Parallel Streams. The spliterator interface is not so easy to implement. You have 4 methods to implement and 4 more default methods that you can redefine. The first four are `trySplit()`, `estimateSize()`, `characteristics()` and `tryAdvance()` which is the one called to get the elements one by one. And the 4 default methods are `getExactSizeIfKnown()`, `forEachRemaining()`, `hasCharacteristics()` and `getComparator()`.

```java
public interface Spliterator<T> {
    boolean tryAdvance(Consumer<? super T> action);
    long estimateSize();
    int characteristics();
    Spliterator<T> trySplit();

    default void forEachRemaining(Consumer<? super T> action) {
        do { } while (tryAdvance(action));
    }
    default long getExactSizeIfKnown() {
        return (characteristics() & SIZED) == 0 ? -1L : estimateSize();
    }
    default boolean hasCharacteristics(int characteristics) {
        return (characteristics() & characteristics) == characteristics;
    }
    default Comparator<? super T> getComparator() {
        throw new IllegalStateException();
    }
}
```

One last word, understanding how all this is working can be very interesting for your application but that will be for another time
</details>

## 186. How can you get an instance of a Class?
<details>
  <summary>Short Answer</summary>

There are actually 4 ways to do that, at least, depending on what you have
</details>
<details>
  <summary>Less Short Answer</summary>

If what you have is an object, then you can call `getClass()` on it which is also working for arrays. Second, you can use the `.class` syntax that works for object types and primitive types. If what you have is the name of a class you can call `Class.forName()` and pass it as a parameter. It also works with Arrays. To get the class instance that represent a primitive type, you can also use the TYPE constant defined in all the wrapper types. And starting with the JDK 22, you can get the class that represent a primitive type with the method `Class.forPrimitiveType()`

```java
var s = "one";
Class<?> s1 = s.getClass();

var ints = new int[]{1, 2, 4};
Class<?> c2 = ints.getClass();

// Or
Class<?> c3 = String.class;
Class<?> c4 = boolean.class;

// Or
Class<?> c4 = Class.forName("java.lang.String");
Class<?> c5 = Class.forName("[I");

// Or
Class<?> c6 = Long.TYPE;
Class<?> c7 = Class.forPrimitiveType("long");
```

One last word, you can also get classes from other classes with `getSuperClass()` or `getInterfaces()`
</details>

## 187. What does it mean to capture a variable?
<details>
  <summary>Short Answer</summary>

It means that you have a local class that references a variable from its enclosing method
</details>
<details>
  <summary>Less Short Answer</summary>

Starting with the JDK 8, local classes can capture final variables. These variable can also be effectively final which means that the compiler added the `final` keyword for you. It is only possible if you do not modify this variable in your code. Odds are that you will do that with Lambda expressions and in that case this Lambda is called the capturing lambda.

```java
var limit = 10;
Predicate<String> shorter = s -> s.length() < limit;

// Error
var limit = 10;
limit++;
Predicate<String> shorter = s -> s.length() < limit; // ERROR
```

One last word, there is a very good reason why Lambda Expressions can only capture final variable that is values and not modifiable variable that has to do with concurrency but that will be for another time
</details>

## 188. What is Serialization?
<details>
  <summary>Short Answer</summary>

A way to save graphs of objects in files or to send them over the network.
</details>
<details>
  <summary>Less Short Answer</summary>

Serialization used to be one of the killer features of the Java platform. It turns out that now this situation changed. There are several security problems with it. For instance, deserializing an object does not call any of its constructors, thus bypassing any validation rules and so it can be used by some malicious code to inject corrupted objects in your application.

One last word, there are several ways to protect your application against that. First you can use records. Deserialization calls the canonical constructor of records, and then you can use deserialization filters at the JVM level but that will be for another time.
</details>

## 189. What does happens-before mean?
<details>
  <summary>Short Answer</summary>

It has to do with the concurrency.
</details>
<details>
  <summary>Less Short Answer</summary>

There are several references to happen-before links in the JavaDoc, for instance the Future interface tells you that the actions taken by the asynchronous computation happen-before actions following the corresponding `future.get()`. A problem may occur if you modify your variable and that this variable is read by another thread. Each thread operates on its own CPU cache. You need a special operation to make sure that the modification you made is visible from all the other CPU caches and this special operation is triggered by the fact that the happen-before link exists between the write operation and the read operation.

One last word, your only source of information should be the Chapter 17 of the Java language specification
</details>

## 190. When can you use finalize()?
<details>
  <summary>Short Answer</summary>

Never
</details>
<details>
  <summary>Less Short Answer</summary>

Never. Any code you put in finalize is most of the time buggy, useless or both. Don't try to have the garbage collector by clearing your collections or your map. First, the garbage collector is smart enough to do it itself and second, you may have race conditions in this code that may lead to NullPointerException among other nasty bugs. Don't close your resources in finalize because they may never be closed, prefer the try with resources pattern which is much safer.

One last word, as of now finalize() is deprecated for removal. Maybe it will stay there, but at some point the garbage collector will not call it anymore so stop overriding this method. 
</details>

## 191. How can you skip elements in a Stream?
<details>
  <summary>Short Answer</summary>

There is a method for that
</details>
<details>
  <summary>Less Short Answer</summary>

You can call `skip()` on a stream and pass the number of elements you need to skip as an argument. That being said, there are several caveats you need to be aware of. For instance, skipping elements only makes sense for ordered stream. If you stream a list or the lines of a text file, then calling `skip(2)` skips the first 2 elements of your list or the first two lines of your text. Skipping elements on a non-ordered stream leads to unpredictable results.

```java
// Ordered
var ints = List.of(3, 4, 5, 1, 2);
var skipped = ints.stream().skip(3).toList();
// [1, 2]

// Non-ordered
var ints = Set.of(3, 4, 5, 1, 2);
var skipped = ints.stream().skip(3).toList();
// [2, 3]
```

One last word, skipping may be costly to call on parallel streams because you may need to have inter-thread communication to track the first elements you want to skip and there is another overhead in doing that
</details>

## 192. What is an Anonymous Class?
<details>
  <summary>Short Answer</summary>

A class that does not have a name.
</details>
<details>
  <summary>Less Short Answer</summary>

The syntax allows you to create the class and its instance at the same time. It's useful when you need to quickly implement an interface or extend a class in your code. There are cases where an anonymous class can be written as a `lambda` but not always. A lambda implements a Functional Interface and an anonymous class can extend anything. You cannot create a constructor in anonymous class, but you can use an instance block if you need to do some initialization.

```java
var counter = new Object() {
    private int count = 10;

    void inc() {
        count++;
    }
};
counter.inc();
System.out.println(counter.count);
// > 11
```

One last word, you can use anonymous classes in conjunction with the `var` keyword, which give you access to the associated non-denotable type but that will be for another time
</details>

## 193. How can you read the Gzip compressed file?
<details>
  <summary>Short Answer</summary>

There is a class for that.
</details>
<details>
  <summary>Less Short Answer</summary>

This class is the `GZIPInputStream` and it takes another input stream as a constructor argument so it's actually a decoration on another input stream. Along with `GZIPOutputStream`, this class allows you to read and write data compressed in the gzip format. Note that, the gzip algorithm supports streaming, meaning that you can get the uncompressed data while you are reading the compressed stream. You can do that with the different `read()` methods available.

```java
try (
    var is = Files.newBufferedInputStream(path);
    var gzis = new GZIPInputStream(is);
) {
    ... = gzis.read(...);
}
```

One last word, Java I/O also supports the ZIP file format, which allows you to compress directory trees but that will be for another time
</details>

## 194. What is a LinkedHashSet?
<details>
  <summary>Short Answer</summary>

A Set with linked elements.
</details>
<details>
  <summary>Less Short Answer</summary>

This set maintains links between its element so that it maintains the iteration order. I f you add C,A,B,B in a HashSet,   the second B is not added and if you iterate over the elements of the set, you will get A,B,C because a HashSet does not maintain in the order of its elements. If you do the same with LinkedHashSet, you will get C,A,B because LinkedHashSet does what is needed to maintain this order. 

```java
var set1 = Set.of(10, 20, 30, 40, 50);
// > [30, 40, 50, 10, 20] -> will vary

var ints = List.of(10, 20, 30, 40, 50);
var set2 = new HashSet<>(ints);
// > [50, 20, 40, 10, 30] -> stable

var set3 = new LinkedHashSet<>(ints);
// > [10, 20, 30, 40, 50] -> stable
```

One last word, starting with the `JDK 21` LinkedHashSet implements `SequenceSet` which brings new methods like direct access to the first and last element of the SequenceSet and a `reversed()` method
</details>

## 195. What is an Intermediate Collector?
<details>
  <summary>Short Answer</summary>

A collector
</details>
<details>
  <summary>Less Short Answer</summary>

The Collectors Factory class gives you a bunch of pre-made, ready-to-use collectors,  and some of the factory methods models Stream intermediate operations like mapping, filtering or flat mapping. These are called intermediate collectors but then there is a problem because a Collector models a terminal Stream operation so these Factory methods also take another collector to compose the mapping operation for instance with this other collector. You can then create complex Collector compositions ending with a terminal collector like `toList()` or `counting()`

```java
var toList = Collectors.toList();
var counting = Collectors.counting();

var mapping = Collectors.mapping(s -> s.length(), toList);
var filtering = Collectors.mapping(s -> s.length() < 5, counting);
```

One last word, The Collector API is quite complex but also very powerful. You should definitely check it out and we will talk more about it in the future
</details>

## 196. What is the HashTable?
<details>
  <summary>Short Answer</summary>

Something you should not be using anymore.
</details>
<details>
  <summary>Less Short Answer</summary>

HashTable was created in the early days of the JDK before the introduction of the Collections framework. The implementation is very similar to `HashMap`, apart from the handling of Hash Collision which is not as efficient and from the fact that all the map methods are synchronized, so if you do not need synchronization HashMap is always a better choice and if you do then `ConcurrentHashMap` is also a better choice.

```java
// DON'T
var table = new Hashtable<>();

// not concurrent
var map = new HashMap<>();

// concurrent
var concurrentMap = new ConcurrentHashMap<>();
```

One last word, be careful because HashTable does not support null values and if you try to put a null key you will get a `NullPointerException`. HashMap supports null keys and null values, even if it may not be the greatest idea

</details>

## 197. What is the Consumer?
<details>
  <summary>Short Answer</summary>

A functional interface
</details>
<details>
  <summary>Less Short Answer</summary>

This functional interface models a Lambda that takes a single parameter and does not return anything. The Consumer is what you pass to the `forEach()` method that you have on the streams and the collections. You can compose consumers thanks to `andThen()` default method on the consumer interface so you can create one consumer from two others just by calling `print.andThen(log)` for instance

```java
@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);
}

var stream = Stream.of(1, 2, 3);
stream.forEach(s -> System.out.println(s));

Consumer<String> print = s -> System.out.println(s);
Consumer<String> log = s -> Logger.info(s);
Consumer<String> printThenLog = print.andThen(log);
```

One last word, the `java.util.function` package also gives you a `biConsumer` that takes two parameters instead of one and specialize consumers: `intConsumer`, `LongConsumer` and `DoubleConsumer`

</details>

## 198. How can you read chars from a binary stream?
<details>
  <summary>Short Answer</summary>

There is a class for that
</details>
<details>
  <summary>Less Short Answer</summary>

The class is `InputStreamReader` which extends `Reader` so it can read characters and that takes an InputStream as a constructor argument so InputStreamReader decorates an existing InputStream, reading its binary content and exposing it as characters. By default, the characters you read are decoded using the default charset. Starting with the JDK 18 this charset is UTF-8.

```java
try (
    var is = Files.newBufferedInputStream(path);
    var reader = new InputStreamReader(is);
) {
    String s = reader.read(...);
}

try (
    var is = Files.newBufferedOutputStream(path);
    var write = new OutputStreamWriter(is);
) {
    ... = reader.read(...);
}
```

One last word, you also have an `OutputStreamWriter` class that extends `Writer`, so that it can write characters and strings on the OutputStream it is built on neat
</details>

## 199. What is a Cyclic Barrier?
<details>
  <summary>Short Answer</summary>

A class from `java.util.concurrent`
</details>
<details>
  <summary>Less Short Answer</summary>

A cyclic barrier is there to synchronize a set of thread and that can release them once they are all waiting on this barrier. You create a CyclicBarrier by giving it the number of threads that will synchronize on it, then each thread should call `barrier.await()` and blocks on this call. When the right number of calls to await has been issued, then the barrier opens, releasing all the blocked threads and because it is cyclic, the barrier will close and you can open it by calling await() again.

```java
var barrier = new CyclicBarrier(3);
Runnable task = () -> {
  try {
      // do something
  } catch (Exception e) {
      // application exceptions
  } finally {
      barrier.await();
      // barrier exceptions
  }
};
```

One last word, cyclic barriers may be interesting if you need to conduct some processings in parallel but you should prefer parallel streams if you can use them
</details>

## 200. What is the Heap Memory?
<details>
  <summary>Short Answer</summary>

The memory managed by your garbage collector.
</details>
<details>
  <summary>Less Short Answer</summary>

The memory used by the JVM is made of several parts. The Heap Memory is the one in which your objects are stored. When you call a `new ArrayList()` for instance, what you get is a reference to some piece of memory that lives in a heap memory. Then, when you do not need this ArrayList anymore, the garbage collector will detect it and will reclaim it to use it for other objects. There are several strategies implemented by different garbage collectors, depending on what you need for your application.

```java
// may be off heap
var buffer = ByteBuffer.allocateDirect(size);

// Memory api
try(var arena = Arena.ofconfined()){
    MemorySegment segment = arena.allocate(size)
}
```

One last word, there is also an off-heap memory not managed by your garbage collector. The JDK gives you two apis to access it; ByteBuffer and the Memory API but that will be for another time
</details>

## 201. How is the reduce() method working?
<details>
  <summary>Short Answer</summary>

It reduces the elements of a Stream
</details>
<details>
  <summary>Less Short Answer</summary>

There are two reduce() methods on the Stream interface; the first one takes only the reduction operation in the form of a Lambda expression. The first element and the second element of the stream are passed to this Lambda, then the result and the third element then the result and the fourth until all the elements of the Stream are consumed. The second overload takes the identity element of your reduction operation. This identity element is then used as the first element of the reduction. If your stream is empty, and you gave an identity element then this element is returned if not then the reduction is undefined reason why the reduction is an empty optional

```java
// reduce
var result = Stream.of(1, 2, 3, 4).reduce((i1, i2) -> i1 + i2);
// 1 + 2 -> 3
// 3 + 3 -> 6
// 6 + 4 -> 10

var result = Stream.of(1, 2, 3, 4).reduce(0, (i1, i2) -> i1 + i2);
// 0 + 1 -> 1
// 1 + 2 -> 3
// 3 + 3 -> 6
// 6 + 4 -> 10

var result = Stream.<Integer>of(1, 2, 3, 4).reduce(0, (i1, i2) -> i1 + i2);
// 0

Optional<Integer> result = Stream.<Integer>of(1, 2, 3, 4).reduce((i1, i2) -> i1 + i2);
// Optiional.empty
```

One last word, that's why you need optionals in Java to have correct reductions
</details>

## 202. What are the Primitive types in Java?
<details>
  <summary>Short Answer</summary>

They are 7 of them
</details>
<details>
  <summary>Less Short Answer</summary>

There are 4 integer types `byte`, `short`, `int`, `long` then 2 for floating-point numbers; `float` and `double` and `char` for characters. Primitive types are values, so they are not references. A primitive type can never be null. There are all associated with a wrapper type, which is a class with the same name. You can check these classes for very useful methods on them like parsing, valueOf() and compare()

```java
// integer types
// bytes    8 bits
// short    16 bits
// int      32 bits
// float    64 bits

// floating-point types
// float    32 bits
// double   64 bits

// character
// char     16 bits

// Parsing
var d = Double.parseDouble("3.14");
var i = Integer.parseInt("314");
// Comparing
int order = Float.compare(f1, f2);
```

One last word, operating on primitive types is super fast. No indirection, no pointer chasing. This is what you need to get the best performance, and this is what the Valhalla project aims to bring for object types, but that will be for another time.
</details>

## 203. What is an Optional?
<details>
  <summary>Short Answer</summary>

A wrapper type that can be empty
</details>
<details>
  <summary>Less Short Answer</summary>

Optionals are there to correctly handle reduction in the case of empty streams. In that case, you need to return the identity element of your reduction operation. You need that because if you combine this result with the reduction of another non-empty stream, you still need the correct result. The problem is that many reductions do not have an identity element that, the case for `max()`, `min()` or `average()`. Returning an empty optional is a way to solve this issue

```java
var stream1 = IntStream.of(-1, -2, -3);
var stream2 = IntStream.of();
var max1 = stream1.max();
var max2 = stream2.max(); // 0?
var max = max(max1, max2); // 0???
```

One last word, even if you never stream empty collections, you may still have to deal with filter operations or parallel streams and both can produce empty streams without you realizing it
</details>

## 204. What is an Expression?
<details>
  <summary>Short Answer</summary>

Something that produces a value.
</details>
<details>
  <summary>Less Short Answer</summary>

An expression is a combination of any operands, operators or method calls that in the end produces a single value. There are language constructs in Java that are not expressions that the case for the `if-else` or the `while` statements. The `switch` used to be a statement, but is now also an expression as for the JDK14 and it is suddenly much more useful. You can switch on Integer types(not longs), enumerations, strings and types

```java
var i = 0;
var j = i++;
var s = "Hello";
var l = s.length();

while(i++ < 10) {
    ...
}

var day = ...;
switch(day) {
    case SATURDAY:
    case SUNDAY:
        println("Week-end");
}

var result = switch(day) {
case SATURDAY, SUNDAY -> "Week-end";
default -> "Week-end";
};
```

One last word, creating switch expressions on seal types is part of the Data Oriented Programming Paradigm, currently being implemented in Java, super interesting but that will be for another time
</details>

## 205. What is the ByteBuffer?
<details>
  <summary>Short Answer</summary>

A class from `java.nio`
</details>
<details>
  <summary>Less Short Answer</summary>

`NIO` stands for New Input/Output that was new in 2002 so it's now called Non-Blocking IO. A ByteBuffer can be used to allocate elements on the off-heap memory and to map files in memory. They suffer from several caveats. First, they are indexed with ints. And second, they can't be closed explicitly, meaning that you cannot deallocate the off-heap memory: This class is now superseded by the `MemorySegment` class indexed with Longs. MemorySegment are created by Arenas that you can close to deallocate them

```java
var byteBuffer = ByteBuffer.allocateDirect(10);
var segment = Arena.ofConfined().allocate(10); // Long

try(var arena = Arena.ofConfined()) {
    var segment = arena.allocate(1_024L);
    ...
} // close() deallocate segment
```

One last word, MemorySegments and Arenas are part of the JEP-454 but that will be for another time
</details>

## 206. What is a non-denotable type?
<details>
  <summary>Short Answer</summary>

A type inferred by the compiler
</details>
<details>
  <summary>Less Short Answer</summary>

A non-denotable type is created by the compiler in several places. One of them is when you create an anonymous class. They are also used for intersection types, you can check the JEP-286 for more details and examples. You can use the inferred type of an anonymous class with the `var` keyword. In that case, you have access to the fields and methods of the anonymous type. You can use this feature to create mutable boxes for instance, which will be much more efficient than using an atomic variable

```java
var counter = new Object() {
    int count = 0;
};
counter.count++;
println("count = " + count);
```

```java
var countingCollector = Collector.of(
    () -> new Object() {int count = 0;},
    (box, element) -> box.count++;
    (box1, element1) ->{
        box1.count += box2.count;
        return box1;
    },
    box -> box.count;
);

var count = Stream.of(0, 1, 2, 3).collect(countingCollector);
println("count = " + count);
// > count = 4
```

One last word, atomic variables are costly performance wise, and they are there to handle concurrency. You should not use them outside of this context
</details>

## 207. What is the difference between a Zip and a Gzip stream?
<details>
  <summary>Short Answer</summary>

Gzip can compress a single file, Zip can compress a full directory tree
</details>
<details>
  <summary>Less Short Answer</summary>

Both are built on the same compression algorithm called `deflate`. Both are modeled by their own input and output stream classes, but zip is a little hairy to use. You first need to create zip entries for directories and files, then right after adding a file entry you need to add the content of that file. Reading this content mirrors this procedure. You first need to discover the entries, then read the files.

```java
var path = Path.of(...);
try(
    var os = Files.newOutputStream(path);
    var zos = new ZipOutputStream(path);
    var printer = new PrintWriter(path);
){
    zos.putNextEntry(new ZipEntry("dir1/"));
    zos.putNextEntry(new ZipEntry("dir2/file.txt"));
    printer.println("Hello!");
}
```

One last word, you can actually create a file system for that, and then you can just create directories and copy files to this file system, normally much simpler.
</details>

## 208. What is a Sequenced Map?
<details>
  <summary>Short Answer</summary>

An interface
</details>
<details>
  <summary>Less Short Answer</summary>

It is a nice addition to the Collections Framework in a `JDK 21`. It models Map that have a defined encounter order. Because this order exists, you can get the first entry or the first key or the last entry or last key. SequenceMap gives you other methods like `reversed()` that gives you a reversed view on the map. No copy is made. Implementation wise: TreeMap and LinkedHashedMap are both SequencedMap.

```java
// getting the first element
var firstEntry = map.firstEntry();
var firstKey = map.sequencedKeySet().first();

// getting the last element
var lastEntry = map.lastEntry();
var lastKey = map.sequencedKeySet().last();

// reversed
var reversedEntries = map.reversed();
var reversedKey = map.sequencedKeySet().reversed();

// implementations
TreeMap<K, V>
LinkedHashedMap<K, V>
```

One last word, Sequence Collection and SequenceSet have also been added along with the SequencedMap interface. That's the `JEP-431` that you can check for all the details, design decisions and examples.
</details>

## 209. What is the Void type?
<details>
  <summary>Short Answer</summary>

A class
</details>
<details>
  <summary>Less Short Answer</summary>

This class is used in a Reflection API. The Reflection API gives you access to the return type of method that can be void. Because the `getReturnType()` returns a Class, this Void type was added to model this type. You could call that a dirty hack. That being said, you cannot create an instance of this type, and you cannot get anything of this type so apart from this use in the Reflection API and also in the MethodHandle API by the way, there is not much you can do with it.

```java
Class<Void> returnType = List.class
    .getMethod("clear")
    .getReturnType();

void process(Object o) {
    if (o instanceof Void v) {
        // always false!
    }
}
```

One last word, the compiler lets you use void in an instanceof or in a switch on types, but that's pretty useless because the result will always be false so don't do it.
</details>

## 210. Why are Vector and HashTable not deprecated?
<details>
  <summary>Short Answer</summary>

There's no short answer to this one.
</details>
<details>
  <summary>Less Short Answer</summary>

These classes are there to stay for backward compatibility reasons. Removing them would break some old code. Deprecating something creates a warnings at compile time telling you, "Hey, this isn't unsafe to use. It will be removed in the future". That's not the case for `Vector`s and `HashTable`s. These classes are old but certainly not unsafe. Using them is not great but not harmful. Removing them could be harmful

```java
// don't use
Vector<E>
Stack<E>
HashTable<K, V>
// use (concurrent)
CopyOnWriteArrayList<E>
Collections.synchronizedList(list)
Vector<E> // yes
ArrayBlockingQueue<E>
ConcurrentHashMap<K, V>
// Collection, not a list
ConcurrentLinkedQueue<K, V>

// use
ArrayList<E>
ArrayDeque<E>
HashMap<K, V>
```

One last word, maybe in a future there will be a way to advertise that there is a better pattern than these, in your IDE for instance, without generating compiler warnings. That would be great
</details>

## 211. What does late binding mean?
<details>
  <summary>Short Answer</summary>

It has to do with knowing what method should be called at runtime.
</details>
<details>
  <summary>Less Short Answer</summary>

When you call an interface method in your code or any method that can be overridden, the compiler cannot tell which method would be called at runtime since it depends on the concrete type you have. Thus the name: late binding, which means that your method call is bound to an implementation only at runtime. Early binding means that this binding can be resolved at compile time. That's the case when you call a particular overload of a method.

```java
int size(List<String> strings) {
    // strings is a list
    return strings.size();
}

// binds to ArrayList.size()
var s1 = size(new ArrayList<>());

// binds to LinkedList.size()
var s1 = size(new LinkedList<>());
```

One last word, late binding occurs when you call a method that can be overridden. It has a cost but can be optimized in some cases.
</details>

## 212. How is Stream.distinct() working?
<details>
  <summary>Short Answer</summary>

It removes the duplicates from the stream.
</details>
<details>
  <summary>Less Short Answer</summary>

Internally distinct adds the elements of the stream in a `HashSet`. When you add an element to a HashSet, the `add()` method returns the boolean. If this boolean is false it means that the element was not added because it was already in HashSet and in that case distinct() does not push this element to the downstream. If it is true this element is immediately pushed to the downstream because it was not in a HashSet so internally, distinct() bufferizes all the different elements of your stream.

```java
var map = new HashMap<String, Integer>();
map.put("one", 1);
map.put("two", 2);
map.put("four", 3);

// UNORDERED stream
var distinct = map.value().stream().distinct().toList();
// > [3, 1, 2]

var ints = List.of(1, 2, 1, 3, 3, 2);

// ORDERED stream
var distinct = ints.stream().distinct().toList();
// > [1, 2, 3]
```

One last word, if you call distinct() on an `ORDERED` stream then a `LinkedHashSet` is used instead of a regular HashSet to preserve the order of your stream precisely.
</details>

## 213. What does capturing a variable mean?
<details>
  <summary>Short Answer</summary>

Capturing is used when a Lambda refers to a field or a local variable.
</details>
<details>
  <summary>Less Short Answer</summary>

A Lambda expression can refers to the fields of a class it is declared in and to the local variables of the method it is declared in. In case your local variable is not declared `final`, the compiler will try to make it final for you and if it can, the viable becomes effectively final and you can capture it. If it can't, then you get the compiler error.

```java
class Box {
    // non-final
    int value;

    Supplier<Integer> box() {
        return () -> value;
    }
    
    Supplier<Integer> box() {
        int value = 3;
        // value becomes effectively final
        return () -> value;
    }
    
    Supplier<Integer> box3() {
        int value = 3;
        value++;
        // value can not be effectively final
        // -> COMPILER ERROR
        return () -> value;
    }
}
```

One last word, returning a capturing lambda can expose the captured state to race conditions. Local variables are never subject to race conditions in Java, reason why you can't capture them if they are not final.
</details>

## 214. How can you create temporary files?
<details>
  <summary>Short Answer</summary>

There is a flag for that
</details>
<details>
  <summary>Less Short Answer</summary>

The factory methods from the `Files` factory class can take `Standard Open Options` as parameters. One of them is called, `DELETE_ON_CLOSE`. If you pass it, the JVM will try to delete the corresponding file when you close this writer or this OutputStream, if you don't close it and it's a mistake, you should close it then it will try to delete it when you exit your application.

```java
var path = Path.of(...);
try(
    var writer = Files.newBufferedWriter(path, StandardOpenOption.DELETE_ON_CLOSE)
){

} // tries to delete path on close()
```

One last word, you should use this option with caution as you can't be sure that some other outside process opened your file, so deleting it may be either impossible or dangerous or both
</details>

## 215. What is Collection.retainAll() working?
<details>
  <summary>Short Answer</summary>

It computes the intersection of 2 Collections.
</details>
<details>
  <summary>Less Short Answer</summary>

`retainAll()` only keeps the element of this Collection that are also in the Collection you pass as an argument. So to be kept, an element needs to be present in both Collections. `retainAll()` returns a boolean that is true if this collection was modified. So you can only call this method on Collections that are modifiable. `retainAll()` calls `contains()` on the Collection you pass for each element of this Collection. So if you want this call to be efficient, you should pass HashSet to retain all.

```java
var ints = new ArrayList<>(List.of(1, 2, 3, 4));
var others = List.of(3, 4, 5, 6);
ints.retainAll(others);
// > [3, 4]

// Set Operations
addAll(other); // Union
removeAll(other); // Complement
retainAll(other); // Intersaction
```

One last word, there are 3 methods to deal with sets in the Collection Framework, `addAll()` for the union, `removeAll()` for the complement and `retainAll()` for the intersection
</details>

## 216. What does tearing mean?
<details>
  <summary>Short Answer</summary>

It has to do with concurrency and 32 bits vs 64 bits machines.
</details>
<details>
  <summary>Less Short Answer</summary>

As you know, some types are stored on 64 bits. On a 64 bits machine, writing a long or a double in memory is done in one operation but on the 32bits machine, you need 2 write operations to write a full long. If you're not cautious in a multi-thread environment, the thread during the write operations can be interrupted. It means that some other thread could see an intermediate state where only the 32 first bits have been updated but not the last. This is what tearing is.

```java
// 1 write op
var i = 0xFFFE;

// 1 write op on 64 bits
// 2 write ops on 32 bits
var l = 0xFFFE_FFFE;
l += 0x0001_0001;

// on 32 bits; you could read 0xFFFF_FFFE or 0xFFFE_FFFF 
```

One last word; you can prevent that using `synchronization`, but it has a cost.
</details>

## 217. What is a stream builder?
<details>
  <summary>Short Answer</summary>

A builder for streams.
</details>
<details>
  <summary>Less Short Answer</summary>

You can build stream by using a `Stream.Builder` builder. The pattern is the following; first, you need to create this builder with the `builder()` factory method and second, you can add object to it with the `add()` calls that you can chain or call `accept()`. Once you're done adding elements, you can call `build()` to create your stream, and you can only call build once, and then you can use this stream normally. Note that this stream is ordered and can accept any value, including null values.

```java
var builder = Stream.builder();
builder
    .add(1)
    .add(2)
    .add(3);

builder.accept(4);
builder.accept(5);
// only once
var stream = builder.build();
```

One last word, this is useful when you can only generate your objects one by one. You do not need to put them in an array or collection. You can rely on the internal `SpinedBuffer` of this builder. Neat.
</details>

## 218. How can you stream the content of a text file?
<details>
  <summary>Short Answer</summary>

There are methods for that.
</details>
<details>
  <summary>Less Short Answer</summary>

There are 2 patterns to do that depending on what you have. If what you have is a `Path`, then you can call the `lines()` method of the Files factory class and pass this path as an argument, and if what you have is a `BufferReader`, then you can call `lines()` directly on it. Note that, this lines method does not exist on regular Readers. What you get is a Stream of the lines of your text file. The nice thing is that the Stream interface is itself `AutoClosable`, so you can create this stream in a try with resources statement. It will close this stream, then in turn calls the `close()` method of the underlying Reader.

```java
var path = ...;
try(var lines = Files.lines(path)){
    // do something with lines
}// close the stream and the file

try(
    BufferedReader reader = ...;
    var lines = reader.lines(path);
){
    // do something with lines
}// close the stream and the file
```

One last word, you also have a `lines()` method on the String class that does the same thing. Neat.
</details>

## 219. What is a ReadWriteLock?
<details>
  <summary>Short Answer</summary>

An interface.
</details>
<details>
  <summary>Less Short Answer</summary>

This has to do with concurrent programming. Read-write lock is useful in situations where you want to allow concurrent reads, but you need to have exclusive write operations. It works better when you have many reads and very few writes. The pattern is the following; you create an instance with the Reentrant Read-Write Lock implementation, then acquire the read or the write lock, use it, and release it in a finally block. Releasing it in a finally block is important because it will be executed even if you have an exception at runtime.

```java
var lock = new ReentrantReadWriteLock();

// Read
var readLock = lock.readLock();
readLock.lock();
try {
    // all read allowed
    // no write
} finally {
    readLock.unlock();
}
```

One last word, you can impose fairness on this implementation, giving the priority to the longest waiting thread, but it has a cost.
</details>

## 220. How is Collection.removeIf() working?
<details>
  <summary>Short Answer</summary>

It removes the elements of a collection using the Predicate passed as an argument.
</details>
<details>
  <summary>Less Short Answer</summary>

The implementation of `removeIf()` varies depending on the collection you have. The default behavior is implemented in the collection interface. It iterates over the elements of the Collection, and remove them if they match the Predicate. This is how it works for `HashSet` or `LinkedList` for instance. Then this method is overridden in `ArrayList`. ArrayList scans and marks all the elements to be removed, then removes them in a second pass.

```java
var ints = new ArrayList<>(List.of(1, 2, 3, 4, 5));
ints.removeIf(e -> e % 2 == 0);
// > [1, 3, 5]

var ints = List.of(2, 2, 2, 2, 2);
// Don't do that!
var list = new ArrayList<>(ints);
list.removeIf(e -> e < list.size());
// > []
```

One last word; be careful your Predicate should not read the collection it works on or throw any exception, because then the behavior could be different on the ArrayList and on other implementations.
</details>

## 221. What is a WeakReference?
<details>
  <summary>Short Answer</summary>

A reference that is managed by the Garbage Collector in a certain way.
</details>
<details>
  <summary>Less Short Answer</summary>

You can create an instance of Weak Reference by passing a reference to any object. What you're doing is actually telling the Garbage Collector, "Hey, if you need some space, you can reclaim this object". If some other object has a regular reference to your object, then calling `get()` will always return your object. But if at some point no regular reference exist anymore, then the Garbage Collector is allowed to set the object your weak reference is pointing to, to null and reclaim this object, calling `get()` will then return null.

```java
var weakRef = new WeakReference<>(user);
var user = weakRef.get();
weakRef.clear();

var noMoreUser = weakRef.get();
// > null
```

One last word; WeakReferences are used in WeakHashMap a map that can be really useful to design caches, but that will be for another time.
</details>

## 222. What is an IdentityHashMap?
<details>
  <summary>Short Answer</summary>

A map.
</details>
<details>
  <summary>Less Short Answer</summary>

When you look for a key in a map, whether it is because you need to put a new key value up here in it or because you are looking for a key, your first compute hash code for that key, and because two keys that are different can still have the same hash code, you compare them. In a regular HashMap, you compare them using their `equals()` method. In an `IdentityHashMap` you use `==`, that is reference equality so if you run this code you will end up with one key-value pair in your map and if you run this one you end up with two

```java
var map = new HashMap<String, String>();
map.put(new String("one"), "one");
map.put(new String("one"), "one");
println("size: " + map.size());
// > size: 1

var map = new IdentityHashMap<String, String>();
map.put(new String("one"), "one");
map.put(new String("one"), "one");
println("size: " + map.size());
// > size: 2
```

One last word; IdentityHashMap can work as long as your keys can be referenced so don't use value objects in them because it will fail when Valhalla is there.
</details>

## 223. How can you limit a Stream?
<details>
  <summary>Short Answer</summary>

There is a method for that.
</details>
<details>
  <summary>Less Short Answer</summary>

Technically speaking, you are not really limiting a stream. What you are saying is that once that stream processed the given amount of object, it should stop and you need to be careful because at each stage, what you get is a new Stream object. If what you need is to skip the first two elements and the last two elements, then if you write the following code what you get is not what you expect because you forgot that the stream on which you call limit consumes only four elements not six so the correct code is this one.

```java
var ints = Stream
        .of(1, 2, 3, 4, 5, 6)
        .skip(2)
        .limit(4)
        .toList();
// > [3, 4, 5, 6]

var ints = Stream
        .of(1, 2, 3, 4, 5, 6)
        .skip(2)
        .limit(2)
        .toList();
// > [3, 4]

```

One last word; `skip()` and `limit()` only make sense on ORDERED streams and both manage an internal mutable counter so don't use them in parallel streams
</details>

## 224. What is a Latch?
<details>
  <summary>Short Answer</summary>

A closed door that will open after you knocked a certain amount of times.
</details>
<details>
  <summary>Less Short Answer</summary>

A `CountDownLatch` is a class used in congruent programming. You create an instance of it by giving it a counter, some threads will call `latch.await()` and some other threads can also call the `latch.countdown()` method, which will decrease the internal counter. Once this counter reaches 0, then the door opens and all the threads blocked on the `await()` calls are free to run. Once a latch opens, it cannot be closed again so you can use a latch for instance to start an application where you need to initialize resources concurrently.

```java
var latch = new CountDownLatch(2);
var t1 = Thread.ofPlatform();
var t2 = Thread.ofPlatform();
var t3 = Thread.ofPlatform();
// in t1
latch.await(); // blocks
// in t2
latch.countdown();
// in t3
latch.countdown();
// -> Latch.await is unblocked
```

One last word; you can check the `CyclicBarrier` class, if what you need is something that you can close again.
</details>

## 225. What is a try with resources statement?
<details>
  <summary>Short Answer</summary>

A great language feature that can close your resources for you.
</details>
<details>
  <summary>Less Short Answer</summary>

The try with resources statement works with any class that implements `AutoClosable` that defines only one method `close()` so you can use it with all your classes that have a `close()` method that returns void. You create your instances as the argument of the `try()` and then when your program exits the following block of code, whether it is with an exception or not all the close() methods are called in the right order

```java
interface MyResource implements AutoClosable {
    void close() {
        // close this resource
    }
}

try(
    var reader = // create a reader
    var resource = new MyResource(reader);
) {
    //var resource = new MyResource(reader); // don't do that
    // play with resource
} catch (Exception e) {
    // Log e
}// calls resource.close() then calls reader.close()
```

One last word; it's important to open all your resources within the `try()` because if you don't, you may have some buffer that will not be properly flushed before the close() is called leading to some loss of data.
</details>

## 226. What is a Gatherer?
<details>
  <summary>Short Answer</summary>

An interface.
</details>
<details>
  <summary>Less Short Answer</summary>

You can see a Gatherer as the equivalent of a `Collector`, but for intermediate operations. The Gatherer API gives you 3 elements; The Gatherer interface, a `gather()` method on the stream interface, and a Gatherers factory class with some ready-to-use gatherers. A Gatherer can model intermediate operations that do not exist on the Stream API. Suppose that you want to remove the duplicates from a Stream of Strings of characters, but ignoring case differences. You can't do it with the stream API, but you can design a gatherer to do that.

```java
// interface
interface Gatherer<T, A, R> {}

// method
interface <R> Stream<R> gather(Gatherer<? super T, ?, R> g){}

// Factory class
class Gatherers{}

var strings = Stream.of("one", "One", "ONE").distinct().toList();
// > ["one", "One", "ONE"]

var strings = Stream.of("one", "One", "ONE").gather(removeDupIngCase).toList();
// > [one]
```

One last word; gatherers can do many things. They can push as many elements as you need to the DownStream, they can manage an internal mutable state, and they can decide to interrupt the Stream or not. Neat.
</details>

## 227. What is type inference?
<details>
  <summary>Short Answer</summary>

A way to deduce the type of a variable or an argument.
</details>
<details>
  <summary>Less Short Answer</summary>

There are many places where you do not declare the type of the variable you use and where the compiler needs to make sure that this type is correct. For instance, when you pass a lambda method, the compiler checks if this lambda matches the type of the parameter this method declares. In the `JDK10` a `var` keyword was added to the language to extend the scope of type inference.

```java
var sum = IntStream.of(1, 2, 3, 4)
        // IntUnaryOperator
        .map(i -> i * 2)
        // IntPredicate
        .filter(i -> i > 3)
        // sum is of type int
        .sum();

// DOES NOT COMPILE
// it must have an initializer
var someVariable;
var someOtherVariable = null;
```

One last word; this `var` keyword can be used only for local variables, not fields nor method parameters, and these variables needs to have an initializer.
</details>

## 228. What is putIfAbsent()?
<details>
  <summary>Short Answer</summary>

A method from the `MAP` interface.
</details>
<details>
  <summary>Less Short Answer</summary>

`putIfAbsent()` takes a key and a value and binds this value to this key under a condition that may be slightly different from what you expect. If you check the source code of `putIfAbsent()` you can see that it does not call `contains()` but `get()` and does the binding `get()` returns null, meaning that if the key is bound to null in your Map, (why would you do that???) then it remaps it with the new value. Some map implementations do not accept null values or keys which is a good idea.

```java
public interface Map<K, V> {
    default V putIfAbsent(K key, V value) {
        V v = get(key);
        if (v == null) {
            v = put(key, value);
        }
        return v;
    }
}
```

One last word; `putIfAbsent()` returns the value that was previously bound to this key, which may be null. So be careful with that.
</details>

## 229. What is a PrintWriter?
<details>
  <summary>Short Answer</summary>

A writer.
</details>
<details>
  <summary>Less Short Answer</summary>

This type is important because it's the type of `System.out` on which you call `println()` to pass "Hello World" to it. It is an extension of the Writer class and it's the class that carries the `printf()` and `println()` methods that takes this nifty, horrible format as a parameter. This format is coming from C and it allows you to format your strings of character to properly display them on text terminals. Yes that was some time ago. By the way, this format is documented in the java.util.Formatter class in case you need it.

```java
class PrintWriter extends Writer {
    PrintWriter printf(...){}
    void println(...){}
}

package java.util;
final class Formatter {}

// Extensions;
// ChoiceFormat
// CompactNumberFormat
// DateFormat
// DecimalFormat
// ListFormat
// MessageFormat
// NumberFormat
// SimpleDateFormat
```

One last word; there are several formatting classes in the JDK. Another one is based on the Format abstract class extended by MessageFormat or SimpleDateFormat. But that will be for another time
</details>

## 230. What is a ThreadLocal variable?
<details>
  <summary>Short Answer</summary>

An old stuff from Java 2.
</details>
<details>
  <summary>Less Short Answer</summary>

ThreadLocal variables were added to allow the passing of arguments from a servlet to another servlet without having to rely on method parameters. That was very useful in the early days of J2EE because a servlet was actually a callback. Now some of the design decisions made at that time do not fit very well with modern frameworks and especially with Virtual Threads. Reason why the Loom project that delivered Virtual Threads in the JDK 21 is developing `ScopedValues`. ScopedValues does the same thing as ThreadLocals but without the drawbacks.

```java
var v = new ThreadLocal<String>();
v.set("Hello Duke");

var duke = v.get();
// DONT FORGET
v.remove();
```

One last word; ThreadLocal variables can be the source of security vulnerabilities in your application, so do not forget to call remove() on them once you're done with them.
</details>

## 231. What is a final field?
<details>
  <summary>Short Answer</summary>

A field with the final modifier on this declaration.
</details>
<details>
  <summary>Less Short Answer</summary>

A final field can be static or not and if it is a static field then it must have an initializer and once it has been initialized, it cannot be modified anymore. For instance, `Mmath.Pi` is a public static final field defined in the Math class. If your field is an instance field, then it needs to be initialized before your object is fully constructed. And once you give a value to it, you cannot change it even from within a constructor.

```java
class Math {
    public static final double PI = 3.141592653589793;
}
class User {
    // useless
    volatile final String name;
    User(String name) {
        this.name = name;
    }
}
```
One last word; final also means that the value of your fields are visible from other threads so you never need to declare a final field volatile, for instance. Neat.
</details>

## 232. How can you sort a Collection?
<details>
  <summary>Short Answer</summary>

well, you can't.
</details>
<details>
  <summary>Less Short Answer</summary>

It does not make sense to sort the Collection because the Collection doesn't have any order. The elements you will see if you iterate over them could change from one iteration to the other. You may be thinking that sorting only makes sense for List, since list are ordered and indeed there is a `sort()` method on the List interface, but you can also sort some sets that are actually `SortedSet` or `NavigableSet`. And this is captured by `Sequenced Collection` added in the JDK 21. `SequencedSet` is an extension of Sequence Collection, and there is also a `SequenceMap` for maps.

```java
interface List<E> {
    void sort(Comparator<E> cmp) {}
}
interface SequencedCollection<E> {
}
interface SequencedSet<E> extends SequencedCollection<E> {
}
```

One last word; ordering and sorting are two different notions. You need ordering to sort, but you can order without sorting.
</details>

## 233. How can you create an Iterable from a Stream?
<details>
  <summary>Short Answer</summary>

There is a pattern for that.
</details>
<details>
  <summary>Less Short Answer</summary>

The idea is to avoid putting all the elements produced by the stream in a Collection or an Array to save on memory. So what you can do is get the Spliterator of the stream and use a factory method of the Spliterator class. An itable is basically a Supplier, so you can pass the construction of this iterator to build your Iterable. This Iterable produces elements as they are pulled by the underlying Stream without buffering them.

```java
var stream = ...;
// NO!
Iterable iterable = () -> stream.toList().iterator();
Iterable iterable = () -> Spliterator.iterator(stream.spliterator());


```

One last word; be careful because a Stream can produce an unbound number of elements so you probably need to protect your application against that.
</details>

## 234. What is a VarHandle?
<details>
  <summary>Short Answer</summary>

An object to access fields.
</details>
<details>
  <summary>Less Short Answer</summary>

You may be thinking that `VarHandle` is the equivalent of MethodHandle, but to access fields. It's actually not the case. You can access fields with MethodHandle and VarHandle was added in the JDK 9, where method handle was added in the JDK 7 so during these 6 years, MethodHandle was used to access fields. What VarHandle gives you is access to fields but with a concurrent semantic like `volatile` or `atomic`. Accessing a field using this mode mimics the fact that the field was defined as a volatile field, for instance.

```java
record User(String name) {}
var user = new User("maria");
var lookup = MethodHandles.lookup();
var varHandle = lookup.findVarHandle(User.class, "name", String.class);
varHandle.accessModeType(AccessMode.GET_VOLATILE);
String name = (String) varHandle.get(user);
// > name = maria
```

One last word; be careful because accessing a field value using a VarHandle ignores the possible volatile declaration on that field.
</details>

## 235. What is a MessageFormat?
<details>
  <summary>Short Answer</summary>

A class.
</details>
<details>
  <summary>Less Short Answer</summary>

MessageFormat works with a pattern and this pattern can be used to format messages from arrays of object or to parse strings of characters to extract the information it contains. There is one major trap in the MessageFormat class. You may be tempted to reuse your MessageFormat and cache them in public static variables for instance. Well, don't do that. A MessageFormat is a mutable object and it's not thread safe so sharing such an instance between threads will produce race-conditions.

```java
var format = new MessageFormat("In {0} Java will turn {1,number}");
var result = format.format(new Object[]{"2025", 30});
// > In 2025 Java will turn 30
```

One last word; date formatting has been superseded by the Date and Time API in the JDK 8, so you may want to check the `DateTimeFormatter` class that will be for another time.
</details>

## 236. What is a Collector built on?
<details>
  <summary>Short Answer</summary>

3 elements plus 1.
</details>
<details>
  <summary>Less Short Answer</summary>

A Collector collects the elements of the Stream in a mutable container. For that, it needs 2 elements; one used to build a mutable container in the form of a Supplier and another one to add an element to this container in the form of a BiConsumer and that's the Accumulator. Then, you can use a Collector in parallel, meaning that several instances of the container may be built in different threads. At some point, you will need to combine them that's the Combiner, which is a BinaryOperator and the last one is made to make your Container non-modifiable, for instance. That's the Finisher and it's a Function.

```java
var collector = Collector.of(
    () -> new ArrayList<>(),
    (list, e) -> list.add(e),
    (list1, list2) -> {
        list1.addAll(list2);
        return list1;
    },
    list -> Collections.unmodifiableList(list)
);
```

One last word; a collector also has Characteristics but that will be for another time.
</details>

## 237. What does escape analysis mean?
<details>
  <summary>Short Answer</summary>

It means performance!
</details>
<details>
  <summary>Less Short Answer</summary>

There are cases in your code where you declare variables that are objects. You already know that they will be destroyed very soon. Objects are a little costly to create and then they need to be garbaged. And sometimes they are just not referenced in your code like the iterator in the for-each pattern or they do not escape the method you're in. In these cases, the JVM may decide not to create these objects. It uses their content where it's needed, but it does not create them.

```java
var ints = List.of(1, 2, 3);

// compiles with an iterator
for (var i: ints){
    // do something with i
}
// that is not in the code!
// What about not creating it at runtime?
```

One last word; on the stack it's called `scalarization`. and on the Heap `flattening`. Something `Valhalla` already does very well .
</details>

## 238. What is getOrDefault()?
<details>
  <summary>Short Answer</summary>

A method from the Map interface.
</details>
<details>
  <summary>Less Short Answer</summary>

`getOrDefault()` takes 2 parameters, a key and a default value. You may be thinking that if the key is not in the Map then it returns the default value. `getOrDefault()` does not check if the key is in the Map with `contains()`, it checks if the `get(key)` returns null. If you have a Map that does not accept null values like `ConcurrentHashMap`, then yes `getOrDefault()` returns the default value you provide if the key is not in the Map. But if your Map accepts null values and that the case for `HashMap` then it also returns the default value in case of a null value.

```java
interface Map<K, V> {
    default V getOrDefault(K key, V value) {
        if (get(key) == null) {
            return value;
        } else {
            return get(key);
        }
    }
}
```

One last word; `getOrDefault()` is aligned with what `putIfAbsent()` does we already talked about that.
</details>

## 239. What is this?
<details>
  <summary>Short Answer</summary>

come on...
</details>
<details>
  <summary>Less Short Answer</summary>

`This` is a keyword of the language that is a reference on the object you are in. Because it is a reference on your instance, you cannot use it in static members of your class for obvious reasons. One fun fact: you can write your methods in that way with `this` as a first parameter. This is actually the trick the compiler is using to give you a this reference in your method. And that's a very good way to write unreadable code and to trick people.

```java
class User {
    String name;
    String getName(User this) {
        return this.name;
    }
    @Override
    String toString(User this) {
        return "User" + this.name;
    }
}
```

One last word; this is also a way to call another constructor from the constructor you are in. There used to be restrictions on the calling of constructors within constructors, which have been lifted for `Valhalla` to have immutable objects, but that will be for another time.
</details>

## 240. How expensive is a Thread?
<details>
  <summary>Short Answer</summary>

A thread is quite expensive.
</details>
<details>
  <summary>Less Short Answer</summary>

It actually depends on your operating system because an instance of a Thread class is a wrapper on a thread provided by your OS. A kernel thread holds several megabytes of memory and may take several milliseconds to create, so yes it is an expensive resource. Reason why application create them when they start and try to keep them alive and reuse them. This leads to the callback-based asynchronous programming model that can work with very few threads.

One last word; all this is valid for kernel threads. Virtual threads on the other hand are like regular objects. You can create them on demand and have as many as you need in your application, but that will be for another time.
</details>

## 241. What is Pattern Matching?
<details>
  <summary>Short Answer</summary>

An old feature from the 70s that is making it to the Java language.
</details>
<details>
  <summary>Less Short Answer</summary>

Pattern Matching was defined by the functional programming people about 50 years ago. So far, there are 2 patterns in Java, `Type Pattern` and `Record Pattern`. When you write `o instanceof string s` what you're really asking is: could this variable o be declared as String s?. And if it is the case, then s, called the pattern variable, is created and you can use it where it makes sense. With Record Pattern you can deconstruct records and create pattern variables for their components.

```java
record Pattern(int x, int y) {}
void someMethod(Object o) {
    if (o instanceof String s) {
        // you can use s here
    }
    if (o instanceof Point p) {
        // you can use p
    }
    if (o instanceof Point(int i1, int i2)) {
        // you can use i1 and i2 here
    }
}
```

One last word; there are more patterns to come, Primitive Type Patterns and Named Patterns but that would be for another time.
</details>

## 242. Why can't you map, filter, reduce a Collection?
<details>
  <summary>Short Answer</summary>

Because you don't want to map, filter, reduce a Collection.
</details>
<details>
  <summary>Less Short Answer</summary>

There are cases where the reduce operation does not need to process all the elements you have to produce a result. If you're looking for the first element, having to map and then filter all the rest of your elements would be a terrible overhead. So mapping everything, then filtering everything before reducing would be a terrible way to implement this algorithm. What you want to do is to take every element through your entire processing pipeline, one step at a time. This is what streams are doing.

```java
var objects = List.of(...);
var mapped = objects.map(...);
var filtered = mapped.map(...);
var result = filtered.findFirst();
// mapped and filtered are not needed!
```
One last word; Eclipse Collections implemented the concept of `Lazy Collections` so if this is what you need please use it.

</details>

## 243. Can you explain the parameterized types of a Collector?
<details>
  <summary>Short Answer</summary>

There are 3 of them.
</details>
<details>
  <summary>Less Short Answer</summary>

But you only need to understand the first one and the last one. The first one is the type of elements this collector can consume. The third type is the type of the element that this Collector can produce. You can leave the second type anonymous, it actually represents the internal container your Collector implementation may use.

```java
Collector<T, A, R> collector;

T: the typed consumed
R: the typed produced

Collector<E, ?, List<E>> toList = Collector.toList();
Collector<E, ?, Map<K, List<E>>> groupingBy = Collector.groupingBy(Function<E, K> mapper);
```

```java
var strings = List.of("one", "two", "three");
var joining = (Collector<CharSequence, StringJoiner, String>) Collectors.joining(", ");
var container = joining.supplier().get();
var accumulator = joining.accumulator();
var finisher = joining.finisher();

strings.forEach(s -> accumulator.accept(container, s));
var result = finisher.apply(container);
// > one, two, three
```

One last word; actually, Collectors do not depend on the stream API. You can use their Supplier, Accumulator and Finisher independently, but that will be for another time.
</details>

## 244. What does volatile mean?
<details>
  <summary>Short Answer</summary>

It has to do with the visibility of fields in a concurrent environment.
</details>
<details>
  <summary>Less Short Answer</summary>

Volatile is a keyword you can put on fields. It means that the read and write operations on this field are volatile reads and volatile writes. And this has to do with the existence of happens-before links between your read operation and your write operations. The Java Specification says that the happens-before link exists between synchronized or volatile reads and synchronized or volatile writes.

```java
class Box {
    volatile int counter = 0;
}
var box = new Box();
Thread.ofVirtual()
      .start(() -> 
        // visible
        box.counter = 1);
Thread.ofVirtual()
      .start(() -> 
        // visible
        println(box.counter));
```

One last word; a volatile reference on a mutable container does not protect the content of this container against race conditions, so be careful with that.
</details>

## 245. How can you compute the median value of an array?
<details>
  <summary>Short Answer</summary>

By using the right algorithm.
</details>
<details>
  <summary>Less Short Answer</summary>

The lazy way of doing it would be to sort the array, then to read the middle index, but it's inefficient. The first step of the quick sort algorithm is to choose the pivot index and move all the smaller elements to the left, meaning that if after doing this, you have split your array in 2 equal parts, it's done. You don't need to go any further. The problem is that you may not have the middle index in one guess, so you need to repeat but only on the largest part that you have on average. You will not have to sort everything, so you will go faster.

```java
// 1 5 3 0 2 6 8 3 2 5 9 
// 1 5 3 0 2 3 2 5 6 8 9 // bad luch
// 1 2 3 0 2 3 5 5 6 8 9 // better!
```

One last word; you can use better strategies if what you need is just something that is close enough. That can be useful, especially if you have a lot of data.
</details>

## 246. How is the toArray() method working?
<details>
  <summary>Short Answer</summary>

There are several toArray() methods; on Collection, Streams and specialized Streams.
</details>
<details>
  <summary>Less Short Answer</summary>

On specialized Streams toArray() builds an array with your number in it, plain and simple. On `Stream<T>`, toArray() builds an array of Objects, but you can also pass a supplier of the given type to produce an array of that type. On Collections, toArray() does the same but it can also take an array of the given type.

```java
int[] ints = IntStream.of(1, 2, 3).toArray();
long[] longs = LongStream.of(1L, 2L, 3L).toArray();
double[] doubles = DoubleStream.of(1D, 2D, 3D).toArray();

Object[] strings1 = Stream.of("one", "two", "three").toArray();
String[] strings2 = Stream.of("one", "two", "three").toArray(String[]::new);

Object[] strings3 = List.of("one", "two", "three").toArray();
String[] strings4 = List.of("one", "two", "three").toArray(new String[0]);
String[] strings5 = List.of("one", "two", "three").toArray(new String[3]);
```

One last word; for Collections passing an empty array may actually be a better idea than passing an array of the right size. This could has to do with the fact that an array must first be filled with zeros, but as usual when it comes to performance measure, don't guess
</details>

## 247. What is an unnamed variable?
<details>
  <summary>Short Answer</summary>

A variable that has no name.
</details>
<details>
  <summary>Less Short Answer</summary>

What could be the use of such a variable? Well, with record patterns you create pattern variable when you deconstruct a record. Creating such variables calls the accessors of your record, which may be costly. So, if you don't need them, you can declare them as unnamed, and they will not be created. You can also use these unnamed variables in Lambda expressions or when you catch exceptions.

```java
record Circle(Point center, double radius) {
    var surface = switch (object) {
        case Circle(Point p, double r) -> Math.PI * r * r;
        // more cases
    };
}

var map = new HashMap<Integer, String>();
List.of("one", "two", "three")
        .forEach(e -> map.computeIfAbsent(e.length(), _ -> new ArrayList<>())
        .add(e)

try(var lines = reader.lines()) {
    // analyze lines
} catch (IOException _) {
    // it failed
}
```

One last word; for record deconstruction, using unnamed variables may also hide a change in your model as well as the use of the var keyword, by the way, so be aware of that before using this feature.
</details>

## 248. What does the reversed() method do?
<details>
  <summary>Short Answer</summary>

It reverses a List.
</details>
<details>
  <summary>Less Short Answer</summary>

Actually, one of the method brought to you by the SequencedCollection API, and this method returns you a view on your SequencedCollection. Since it is a view, if the underlying SequenceCollection is modified, you will see this notification. Note that, for a list this reversed view is also modifiable. Modifying it modifies the underlying list. If what you need is a copy and not a view, you can still pass it to `List.copyOf()` that will happily copy it for you.

```java
var ints = new ArrayList<>(List.of(1, 2, 3, 4));
println(ints);
println(ints.reversed());
ints.add(2, 10);
println(ints.reversed());
// > [1, 2, 3, 4]
// > [4, 3, 2, 1]
// > [4, 3, 10, 2, 1]
ints.reversed().add(2, 10);
println(ints);
// [1, 2, 10, 3, 4]

var copy = List.copyOf(ints.reversed());
```

One last word; be careful though because `List.copyOf()` does not accept null values. Why would you put null values in your collections?
</details>

## 249. Why Java doesn't allow variable capturing?
<details>
  <summary>Short Answer</summary>

Because it would have changed the concurrent programming model.
</details>
<details>
  <summary>Less Short Answer</summary>

A lambda can only capture a final variable, that is a value. It cannot capture a modifiable local variable. If it had been allowed, since this lambda can escape the method it is declared in and sent to different threads it would have exposed these local variables to different threads and then to race conditions, something that does not exist in Java, so the decision was; You can only capture values, not modifiable variables.

```java
void process() {
    int count = 12;
    count++;
    
    // does not compile!
    return () -> count;
}
void process() {
    int count = 12;
    // compiles because
    // count is efficiently final
    return () -> count;
}
```

One last word; there are JVM-based languages that allow the capturing of local variables in lambdas. But when it comes to race conditions, you're on your own.
</details>

## 250. What is a blocking call?
<details>
  <summary>Short Answer</summary>

Something you want to avoid.
</details>
<details>
  <summary>Less Short Answer</summary>

How much time does it take to process a network request/response cycle? Creating a request and analyzing a response takes in the order of the microseconds. Waiting for a network response to come takes in the order of the milliseconds, so it is a thousand times slower. Blocking means that during this time, the threat that is running your request is waiting, doing nothing. It could handle about a thousand requests construction or response analyzes, but it does not.

```java
// 1 microsec to execute this
var jsonRequest = buildRequest();

// 1_000 microsec to get the response during which the thread is doing nothing.
var json = send(jsonRequest);
// 1 microsec to analyze json
var response = analyze(json);

// works fine in virtual threads
```

One last word; the existing solution to overcome this problem is to use reactive programming and avoid the writing of blocking code. The future is to write blocking code but in virtual threads but that will be for another.
time
</details>

## 251. What is a Predicate?
<details>
  <summary>Short Answer</summary>

A Functional interface.
</details>
<details>
  <summary>Less Short Answer</summary>

This interface defines a `test()` method that takes an object and that returns a boolean. It is used in several places in the stream API and the Collections Framework. For instance, in the `filter()` method that can filter a Stream or in the `Collection.removeIf()` method that will remove elements from a Collection. This interface defines default methods to combine predicates with `AND` and `OR`. You can also negate a Predicate with the `negate()` method or the `not()` method which is a factory method that takes another predicate.

```java
interface Predicate<T> {
    boolean test(T t);
}
Predicate<Integer> isPositive = i -> i > 0;
Predicate<String> isEmpty = String::isEmpty;
Predicate<String> isNull = Objects::isNull;
Predicate<String> notNullNotEmpty = Predicate.not(isNull.or(isEmpty));
```

One last word; it is one of the 4 fundamental Functional Interfaces that you need to know, `Consumer`, `Supplier`, `Function` and `Predicate`.
</details>

## 252. What is a WeakHashMap?
<details>
  <summary>Short Answer</summary>

A Map.
</details>
<details>
  <summary>Less Short Answer</summary>

The keys of a WeakHashMap are weak references which can be garbaged if it is not used by anything in your application. Meaning that the size of this map may decrease over time without your application ever calling `remove()`. This is very useful to create caches for instance, because you can add key-value pairs in a WeakHashMap and if at some point your application is running low on memory, the garbage collector can just remove the ones that are not used.

```java
var map = WeakHashMap.<Integer, String>newWeakHashMap(50);
map.put(1, "one");
map.put(2, "two");
map.put(3, "three");
// do a lot of stuff
map.size(); // <- can be < 3!
```

One last word; values in a WeakHashMap are stored using strong references. So if your value has a strong references on its key, your weak hashmap will just behave as a regular HashMap. So, don't do that.
</details>

## 253. How can you use a Collector outside of the Stream API?
<details>
  <summary>Short Answer</summary>

There is a pattern for that.
</details>
<details>
  <summary>Less Short Answer</summary>

A Collector is built on 4 elements. `a supplier`, `an accumulator`, `a combiner`, and `a finisher`. You can apply these elements on a List, for instance. First, you need to create the mutable container. Second, you can accumulate the element of this List in it using the accumulator. And once this is done, you need to call the finisher on the result if you have one, and you're done.

```java
Collector<String, StringBuilder, String> joiner = Collector.of(
    StringBuilder::new,
    StringBuilder::append,
    StringBuilder::append,
    StringBuilder::toString);
var strings = List.of("1", "2", "3");
var sb = joiner.supplier().get();
strings.forEach(s -> joiner.accumulator().accept(sb, s));
var result = joiner.finisher().apply(sb);

//> "123"
```

One last word; Collectors do not depend on the stream API, so you can use them independently. And it's a very powerful API that can model complex processing, just as gatherers. But that will be for another time.
</details>

## 254. What is a StampedLock?
<details>
  <summary>Short Answer</summary>

A lock with an optimistic read mode, among other things.
</details>
<details>
  <summary>Less Short Answer</summary>

A StampedLock locked has 3 modes, `exclusive write` and `non-exclusive read`, which are the 2 modes of `ReadWriteLocks`, plus a third one, `optimistic read`. The stamp you get when you call one of the `lock()` methods must be provided to unlock this StampedLock. Optimistic reads are interesting but also fragile. You need to acquire the lock, check if it is non-zero, read what you need, and then validate what you just read to make sure no write was done from another thread.

```java
var stampedLock = new StampedLock();
var stamp = stampedLock.writeLock();

try {
    // exclusive  write  
} finally {
    stampedLock.unlockWrite(stamp);
}

try(for(;; stamp = stampedLock.tryOptimisticRead()) ){
    if(stamp == 0L)
        continue: retry;
    // read what you need
    if(!stampedLock.validate(stamp))
        continue: retry;
} finally {
    stampedLock.unlockRead(stamp);
}
```

One last word; locks obtained from StampedLock can also be upgraded. For instance, from read lock to write lock.But that will be for another time.
</details>

## 255. How can you create multi-dimensional arrays?
<details>
  <summary>Short Answer</summary>

There is a pattern for that.
</details>
<details>
  <summary>Less Short Answer</summary>

There is a syntax to create and use arrays with multiple dimensions. But under the hood, what you get is an array of references to other arrays that can be stored anywhere in the memory of your application. It is actually working in that way. First, you create an array of references then for each of them, you create another array of the right size. And by the way, this size can vary from one array to the other.

```java
int[][] ints = new int[10][10];
ints[5][5] = 1;

int[][] ints;
ints = new int[10][];

for(int[] subarray: ints) {
    subarray = new int[10];
}
```

One last word; There is no way you can automatically map a large contiguous region of memory to a multi-dimensional array as you can do it in C, for instance. If this is what you need, you will have to write some code.
</details>

## 256. How can you stream the content of a directory?
<details>
  <summary>Short Answer</summary>

There is a method for that.
</details>
<details>
  <summary>Less Short Answer</summary>

The method you want to call is `newDirectoryStream()` declared on the Files factory class. It returns a `DirectoryStream` object. This object is not a Stream but an Iterable. So you can get an Iterator from it. This iterator gives you the guarantee that a call to `next()` that follows a call to `hasNext()` that returned true will not fail. Which when you think about the concurrent nature of file systems is not obvious. Note that the directory you stream is not frozen while you iterate on its content. What you get is the content of that directory. Subdirectories are not explored.

```java
var dir = Path.of(...);
try(var paths = Files.newDirectoryStream(dir)) {
    for(vat path: paths) {
        // do something
    }
} // needs to be closed
```

One last word, you can also pass a filter to the construction of this object to list all the files of a certain type for instance.
</details>

## 257. What is a stack trace?
<details>
  <summary>Short Answer</summary>

An Array.
</details>
<details>
  <summary>Less Short Answer</summary>

All the Exception classes extend Throwable. And when you create an instance of such an object, an array is created that contains all the methods that call the line of code on which this exception was created. Note that this array is filled when the exception is created. Reason why, if you create an exception to report an error and throw it, you'd better call throw new so that the stack trace that you get take you to the right place in your application.

```java
1: var t = new Throwable();
2:
3:
4:
5: t.printStackTrace();
6:
// > java.lang.Throwable at Main.main(Main.java:1)
```

One last word, sometimes the stack trace does not contain all the stacked frames. In extreme cases, you may even have no stack frame at all. That may happen if the VM has no stack trace information.
</details>

## 258. How can you read a ZIP file with the FileSystem API?
<details>
  <summary>Short Answer</summary>

There is a pattern for that.
</details>
<details>
  <summary>Less Short Answer</summary>

Java NIO gives you a `FileSystem` abstract class to model file systems, and one of them can access JAR files that are used in Java applications. You can create such a file system on a zip file and then use it to create files, directories, with the classical Java I/O and NIO patterns and you can do the same to read them. It's exactly like you were writing or reading from a regular disk file system.

```java
var uri = URI.create("jar:file:/dir/archive.zip");
var env = Map.of("create", "true");
try (
    var zipfs = FileSystems.newFileSystem(uri, env);
    // then decorate writer
    var writer = Files.newBufferedWriter(zipfs.getPath("/").resolve("hello.txt"));
) {
    // user writer
}
```

```java
try (
    var zipfs = ...;
    var writer = ...;
    // then decorate writer
    var printWriter = new PrintWriter(writer);
) {
    printWriter.println("Hello World!");
    Path newDir = zipfs.getPath("/").resolve("new-dir");
    Files.createDirectories(newDir);
}
```

```java
try (
    var zipfs = ...;
    var writer = ...;
    Files.list(zipfs.getPath("/").resolve("hello.txt"));
) {
    lines.forEach(System.out::println);
}
```

One last word, as you know, Path objects are actually bound to a specific file system. So when using this pattern, you need to use Path objects or File objects, but created from Paths.
</details>

## 259. Is the String Class an Immutable Class?
<details>
  <summary>Short Answer</summary>

That's actually a trick question. And the correct answer is no.
</details>
<details>
  <summary>Less Short Answer</summary>

You probably think that the string class is a non-modifiable class, which is partly true. What is true is that once you fix the value of a string of characters, you cannot change it. All the methods of the String class, like `toUpperCase()` or `substring()`, actually return another String object that wraps a different array. But there is a mutable field in the string class, which holds the hash code of that string object. This hash code is cached in a field.

```java
class String {
    private final byte[] value;
    private int hash; // mutable field
    
    public String toUpperCase() {
        // some complex computations
        return new String(...);
    }
    
    public String substring() {
        // some complex computations
        var newValue = Arrays.copyOfRange(...);
        return new String(newValue);
    }
    
    public int hashCode() {
        if (hash == 0 && !hashIsZero) {
            // compute hash code
            hash = computedHash;
        }
        return hash;
    }
}
```

One last word, this mutable field makes it so that a String cannot be made a value object with Valhalla. Unless it is changed, but that will be for another time.
</details>

## 260. What is a Virtual Thread?
<details>
  <summary>Short Answer</summary>

A class, that is not public.
</details>
<details>
  <summary>Less Short Answer</summary>

Virtual Threads are an amazing addition to the JDK21. A Virtual Thread is a wrapper on a task you want to submit to a regular thread. This task can be modeled by a Runnable or a Callable. Formally, Virtual Threads can be mounted and unmounted on regular threads, so that they can execute the task that they wrap. And when your task blocks, like when it is waiting for data from the network, the NIO API unmounts the Virtual Thread so that the regular Thread is not blocked. Being able to unmount a task from a Thread was not possible in Java before Virtual Threads, and that's a game changer.

```java
var task = // runnable
var thread = Thread.ofVirtual()
    .unstarted(task);
// this is virtual thread
// task SHOULD be blocking!
thread.start();

var executor = Executors.newVirtualThreadPerTaskExecutor();
// executed in a virtual thread
// task SHOULD be blocking!
var future = executor.submit(task);
```

One last word, Virtual Threads are made to wrap blocking tasks. Forget about using them for anything else.
</details>

## 261. How can you represent time?
<details>
  <summary>Short Answer</summary>

There is a class for that.
</details>
<details>
  <summary>Less Short Answer</summary>

The problem is that there are in fact 2 of them; `java.sql.time` that extends `java.sql.Date` and LocalTime, which is the one you should favor. A LocalTime models an hour, minute, second with a nanosecond precision and with no time zone information. And it's an immutable class. You have factory methods to create a LocalTime, accessors to read the time it carries, methods to create another LocalTime from the one you have, and even with the methods. Neat.

```java
var now = LocalTime.now();
var time1 = LocalTime.of(
    9,  //hours
    15, //minutes
    43  //seconds
);
var minutes = time1.getMinute();
var time2 = time1.plusHours(2);
var time3 = time1.withMinutes(30);
```

One last word, LocalTime is now a value-based class, which is a Valhalla notion. Among other restrictions, you should not synchronize on it. That will be for another time.
</details>

## 262. What is mapMulti()?
<details>
  <summary>Short Answer</summary>

A method from the Stream interface.
</details>
<details>
  <summary>Less Short Answer</summary>

mapMulti() allows you to flat-map a stream without having to create intermediate Streams object, which can be an overhead in your data processing pipeline. You need to call mapMulti() with a lambda that takes 2 arguments; the element of the stream you need to process and an object that models the downstream. When you want to pass an object to the downstream, you need to call `downstream.accept()`. You can call accept() any number of times or not call it at all.

```java
var ints = List.of(1, 2, 3, 4);
var stream = ints.stream().mapMulti((elt, downstream) -> {
    if (elt % 2 == 0) {
        downstream.accept(elt);
        downstream.accept(elt);
    }
});
var result = stream.toList();
// > [2, 2, 4, 4]
```

```java
var ints = List.of(1, 2, 3, 4);
Stream<Object> stream = ints.stream().mapMulti((elt, downstream) -> {
    if (elt % 2 == 0) {
        downstream.accept(elt);
        downstream.accept(elt);
    }
});
List<Object> result = stream.toList();
// > [2, 2, 4, 4]
```

One last word, you need to specify the type of the object you are pushing to the downstream when you call mapMulti(). If you don't, this method will return a stream of objects. Usually, it's not what you want.
</details>

## 263. What is a ConcurrentMap?
<details>
  <summary>Short Answer</summary>

An interface.
</details>
<details>
  <summary>Less Short Answer</summary>

The ConcurrentMap interface has a double rule of defining thread-safety and the atomicity of some operations on Map. It has 2 implementations in a JDK; `ConcurrentHashMap` and `ConcurrentSkipListMap`. Each method defined in this interface can be specified to be atomic. That's the case for `putIfAbsent()` for instance, which cannot be interrupted between the checking of the absence of the key and the binding of this key to the value you provide. Atomicity may also apply to some methods of the Collections you can get from this map; `values()`, `keySet()` or `entrySet()`.

```java
interface ConcurrentMap {}
interface ConcurrentHashMap extends ConcurrentMap {}
interface ConcurrentSkipListMap extends ConcurrentMap {}

putIfAbsent(K key, V value) {
    // equivalent to:
    if(!map.containsKey(key)) {
        return map.put(key, value);
    } else
        return map.get(key);
    // but atomic
}
```

One last word; be careful because some concurrent maps do not accept null keys. Why would you put null keys in a Map?
</details>

## 264. How can you access the off-heap memory?
<details>
  <summary>Short Answer</summary>

There is a whole API for that.
</details>
<details>
  <summary>Less Short Answer</summary>

There are 2 APIs in fact to do that. The first one is really old from Java 4 in 2002 and it's the `ByteBuffer` class. The Panama project brought new patterns to access the off-heap memory based on the use of an `Arena` object. From an Arena, you can get Memory Segments and then read and write data from them. You can do so directly with an offset or with an index. You can also map them to file just like you could with ByteBuffers.

```java
try(var arena = Arena.global()) {
    MemorySegment segment = arena.allocate(1_024L);
    segment.set(
        ValueLayout.JAVA_INT, // Layout
        4L,     // offset
        314     // value
    );
    var value = segment.get(
        ValueLayout.JAVA_INT, // Layout
        4L // offset
    );
}
```

```java
var path = ...;
try(var arena = Arena.global();
    var channel = FileChannel.open(path, ...)) {
    ByteBuffer buffer = channel.map(
        MapMode.READ_ONLY, 
        0, channel.size());
    MemorySegment segment = channel.map(
        MapMode.READ_ONLY, 
        0, channel.size(),
        arena);
}
```

One last word, `ByteBuffers` are indexed with integers and `MemorySegments` with longs. You can also define layouts on them to access their content in a structured way, but that will be for another time.
</details>

## 265. What is a SIZED stream?
<details>
  <summary>Short Answer</summary>

A stream that will produce a known number of elements.
</details>
<details>
  <summary>Less Short Answer</summary>

SIZED is actually a characteristic of a stream. You can read these characteristics from the Spliterator your stream is built on. When you open a stream on a Collection because you know the size of the Collection, you also know that this stream will produce this number of elements. In the case you stream the elements you get when you split a String with a regular expression, it's not the case. So that stream is not SIZED.

```java
var ints = List.of(1, 2, 3, 4);
var stream = ints.stream();
var sized = (stream.spliterator().characteristics() & Spliterator.SIZED) > 0;
// > true

Pattern.compile(" ")
       .splitAsStream(someText);
var sized = (stream.spliterator().characteristics() & Spliterator.SIZED) > 0;
// > false
```

One last word; these characteristics are used to optimize your streams. For instance, calling `toList()` can directly create an array of the right size without having to do any resizing. Neat!
</details>

## 266. What is a deserialization filter?
<details>
  <summary>Short Answer</summary>

It is a filter that you can declare to prevent the deserialization of specific classes.
</details>
<details>
  <summary>Less Short Answer</summary>

Deserialization an unknown stream of data is inherently a dangerous activity. A deserialization filter can prevent instances of classes and graphs of object that are too deep or too complex from being deserialized. You need to implement the `ObjectInputFilter.checkInput()` method with the information you need on the data stream. You can then return a Status that can be ALLOWED, REJECTED or even UNDECIDED.

```java
ObjectInputFilter filter = filterInfo -> {
    // analyze filterInfo for
    // - serial class
    // - depth
    // - references
    // - array Length
    // - stream bytes
    
    // return a status
    // can be
    // ALLOWED REJECTED UNDECIDED
    return Status.REJECTED;
};

// set the filter
ObjectInputFilter.Config.setSerialFilter(filter);
```

One last word; serialization is the source of many security issues. Using records can prevent some of them, so use them wherever you can.
</details>

## 267. How can you get the class of a primitive type?
<details>
  <summary>Short Answer</summary>

There is a pattern for that.
</details>
<details>
  <summary>Less Short Answer</summary>

Primitive types are associated with classes that you need when you want to get a method from a class using the Reflection API. You can use the `int.class` syntax that gives you a class of Integer. But the JDK 22 added a new method on the Class class: called `forPrimitiveName()` that takes the primitive type as a string of characters and that returns you the same object.

```java
class Box {
    int x;

    public void setX(int x) {
        this.x = x;
    }
}
var method = Box.class.getMethod("setX", int.class);
// > void org.paumard.Box.setX(int)
```

```java
Class<Integer> intClass = int.class;
Class<Integer> sameIntClass = Class.forPrimitiveName("int");
```

One last word; so far primitive types are different from object types. This may change in the future once the value types from Valhalla make it to the JDK. You'll even be able to define your own primitive type like floats on 16 bits, but that will be for another time.
</details>

## 268. Why do you need Optional?
<details>
  <summary>Short Answer</summary>

To tell that a method cannot return anything.
</details>
<details>
  <summary>Less Short Answer</summary>

There are cases where you need that. And returning void or null does not tell that you cannot return anything. It's a way of returning nothing, which is different. Because a stream can be computed in parallel, the reduction operation has to be associative. If it was not, the result of your operation would depend on the order in which it has been computed. But then a stream can be empty. What could be the result of the reduction of an empty stream? Well, it has to be the identity element of your reduction operation. But now, what can you do for Min or Max or any reduction that does not have any identity element? The choice is to return an optional that can be empty.

```
A = {1, 2, 3}
B = {4, 5, 6}
C = A U B
Max(C) = Max(Max(A), Max(B))
```

```
A = {}
B = {1, 2, 3, 4, 5, 6}
A U B = B
Max(Max({}), Max(B)) = Max(B)

So Max({}) = Id(Max)
```

One last word. Using optionals in any other context is usually a bad idea. Don't do that.
</details>

## 269. What is a Function?
<details>
  <summary>Short Answer</summary>

A functional interface.
</details>
<details>
  <summary>Less Short Answer</summary>

A Function maps an object of a given type to an object of another type. It is used by the `map()` method of the stream interface. The Function interface also defines a method to chain and compose functions. It also defines a factory methods that return the identity function. There are also specialized functions to avoid the boxing of primitive types when you want to process numbers and the Unary Operator, that is a Function that does not change the type.

``` java
interface Function<T, R> {
    R apply(T t);
}
Function<String, Integer> f1 = s -> s.length();
Function<Integer, String> f2 = i -> "" + i;
Function<Integer, String> f3 = f1.andThen(f2);

Function<String, String> id = Function.identity();
ToIntFunction<String> f5 = s -> s.length();
UnaryOperator<String> f6 = s -> s.toLowerCase();
```

One last word; Function is part of the 4 fundamental Functional Interfaces of the JDK; `Consumer`, `Supplier`, `Predicate` and `Function`. And yes, it's okay to add `Runnable` to the lot, even if Runnable was there long before Java 8.
</details>

## 270. What is a Spliterator?
<details>
  <summary>Short Answer</summary>

An interface.
</details>
<details>
  <summary>Less Short Answer</summary>

A Spliterator is an object on which a stream is built. It has a number of methods to traverse the element of the source, to partition them, and to get information on the source. Writing your own spliterator is not an easy task, and you need to be careful about the behavior of each method. Fortunately, there are many examples in the JDK itself to help you. You can check for instance the `ArrayListSpliterator` or the `HashMap.KeySpliterator` which is the Spliterator of the HashSet.

``` java
interface Spliterator<E> {
    boolean tryAdvance(Consumer);
    void forEachRemaining(Consumer);
    Spliterator<E> trySplit();
    
    long getExactSizeIfKnown();
    long estimateSize();
    int characteristics();
}
```

```java
class ArrayList<E> {
    final class ArrayListSpliterator<E> {}
}
class HashMap<K, V> {
    Spliterator<K> spliterator() {
        return new HashMap.KeySpliterator<>(...);
    }
}
```

``` java
class Pattern {
    Stream<String> splitAsStream(String input) {
        class MatcherIterator implements Iterator<String> {
            ...
        }
        return StreamSupport.stream(
            Spliterators
                .spliteratorUnknownSize(
                  new MatcherIterator(input), ...);
    }
}
```

One last word, a spliterator can produce an unbound number of elements, and you can produce them lazily. You can check the `RandomIntSpliterator` or the `MatcherIterator` used in the `Pattern.splitAsStream` method.
</details>
