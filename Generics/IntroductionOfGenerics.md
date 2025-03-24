# Why Use Generics?

Generics allow you to use **type parameters** in classes, interfaces, and methods, making code **reusable** for different data types while ensuring **type safety**.

### **Benefits of Generics:**

1. **Stronger Type Checking** – Errors are caught at compile time rather than runtime.
2. **Eliminates Casting** – No need for explicit type casting when retrieving values.
3. **Reusable & Type-Safe Code** – Allows writing generic algorithms that work with various data types while maintaining readability and safety.

### **Example Without Generics (Requires Casting)**

```java
List list = new ArrayList();
list.add("hello");
String s = (String) list.get(0);  // Explicit cast required
```

### **Example With Generics (No Casting Needed)**

```java
List<String> list = new ArrayList<>();
list.add("hello");
String s = list.get(0);  // No cast needed
```

Generics make your code **cleaner, safer, and more flexible**! 🚀

actually I want to you give me this .md file format as I can add this as note in github .md file

# Generics type
## A Generic Version of the Box Class

A **generic class** allows defining a class with **type parameters** to make it reusable with different data types.

### **Syntax:**
```java
class ClassName<T1, T2, ..., Tn> { /* ... */ }
```
The **type parameter (`T`)** is introduced within angle brackets (`<>`) and can be used anywhere inside the class.

### **Example: Generic Box Class**
```java
/**
 * Generic version of the Box class.
 * @param <T> the type of the value being boxed
 */
public class Box<T> {
    private T t;  // T stands for "Type"

    public void set(T t) { this.t = t; }
    public T get() { return t; }
}
```

### **Key Benefits:**
1. **Replaces Object with T** – No need for casting.
2. **Works with Any Non-Primitive Type** – Class, Interface, Array, or another Generic Type.
3. **Can Be Extended to Generic Interfaces** – The same concept applies to interfaces.

---

## How and Why `T1, T2, ..., Tn` Are Used in Generic Classes?

In a **generic class**, the type parameters (`T1, T2, ..., Tn`) allow multiple **different** types to be used within the same class. This makes the class more flexible and reusable.

### **Why Use Multiple Type Parameters (`T1, T2, ..., Tn`)?**
1. **Handling Multiple Data Types** – Useful when a class needs to work with more than one type.
2. **Improving Type Safety** – Ensures each type is used correctly without needing casts.
3. **Enhancing Code Reusability** – Reduces duplicate code by using a single class for multiple types.

### **Example: Generic Pair Class (`T1, T2`)**
If we need a class that holds **two different types** of values, we can define:
```java
public class Pair<T1, T2> {
    private T1 first;
    private T2 second;

    public Pair(T1 first, T2 second) {
        this.first = first;
        this.second = second;
    }

    public T1 getFirst() { return first; }
    public T2 getSecond() { return second; }
}
```
#### **Usage Example:**
```java
Pair<String, Integer> pair = new Pair<>("Age", 25);
System.out.println(pair.getFirst());  // Output: Age
System.out.println(pair.getSecond()); // Output: 25
```
- `T1` is replaced with `String`
- `T2` is replaced with `Integer`

### **When to Use More Type Parameters (`T1, T2, T3, ...`)?**
Use multiple type parameters when:
- A class needs to **store multiple types** (e.g., `Pair<T1, T2>`)
- A method requires **multiple generic inputs**
- A generic **map-like structure** (e.g., `Map<K, V>` where `K` is the key type and `V` is the value type)

### **Example: Triple Class (`T1, T2, T3`)**
```java
public class Triple<T1, T2, T3> {
    private T1 first;
    private T2 second;
    private T3 third;

    public Triple(T1 first, T2 second, T3 third) {
        this.first = first;
        this.second = second;
        this.third = third;
    }

    public T1 getFirst() { return first; }
    public T2 getSecond() { return second; }
    public T3 getThird() { return third; }
}
```
#### **Usage Example:**
```java
Triple<String, Integer, Double> triple = new Triple<>("John", 30, 75.5);
System.out.println(triple.getFirst());  // Output: John
System.out.println(triple.getSecond()); // Output: 30
System.out.println(triple.getThird());  // Output: 75.5
```

### **Conclusion**
- Use **`T1, T2, ..., Tn`** when dealing with **multiple different types**.
- **Improves code flexibility, readability, and reusability**.
- Helps **avoid type casting** and makes the code **type-safe**.

Generics make Java code **more powerful and maintainable**! 

## Invoking and Instantiating a Generic Type

To use a generic class, you invoke it with a concrete type, like `Box<Integer>`. This is similar to invoking a method, but instead of passing an argument, you provide a type argument (`Integer` in this case) to the generic class.

**Terminology:**
- **Type Parameter**: The placeholder (`T`) in `Box<T>`.
- **Type Argument**: The specific type you provide (`Integer` in `Box<Integer>`).

The declaration `Box<Integer> integerBox;` doesn’t create an object but defines a reference to a "Box of Integer."

To instantiate it, use:
```java
Box<Integer> integerBox = new Box<Integer>();
```

### The Diamond (<>)

In Java SE 7 and later, you can use the diamond (`<>`) to replace type arguments when invoking a generic constructor, as long as the compiler can infer the type. This simplifies code by eliminating the need to repeat the type.

For example:
```java
Box<Integer> integerBox = new Box<>();
```
### Raw Types

A **raw type** is the name of a generic class or interface without specifying type arguments. For example:
```java
public class Box<T> {
    public void set(T t) { /* ... */ }
}
//This is the raw type of Box<T>:
Box rawBox = new Box();
rawBox.set(8);  // warning: unchecked invocation to set(T)
```

> You also get a warning if you use a raw type to invoke generic methods defined in the corresponding generic type:
```java
Box<String> stringBox = new Box<>();
Box rawBox = stringBox;
rawBox.set(8);  // warning: unchecked invocation to set(T)
```
> The warning shows that raw types bypass generic type checks, deferring the catch of unsafe code to runtime.

### Generic Methods

Generic methods are methods that introduce their own type parameters. This is similar to declaring a generic type, but the type parameter's scope is limited to the method where it is declared. Both static and non-static generic methods are allowed, as well as generic class constructors.

The syntax for a generic method includes a list of type parameters, inside angle brackets, which appears before the method's return type. For static generic methods, the type parameter section must appear before the method's return type.

#### Example

The `Util` class includes a generic method `compare`, which compares two `Pair` objects:

```java
public class Util {
    public static <K, V> boolean compare(Pair<K, V> p1, Pair<K, V> p2) {
        return p1.getKey().equals(p2.getKey()) &&
               p1.getValue().equals(p2.getValue());
    }
}

public class Pair<K, V> {
    private K key;
    private V value;

    public Pair(K key, V value) {
        this.key = key;
        this.value = value;
    }

    public void setKey(K key) { this.key = key; }
    public void setValue(V value) { this.value = value; }
    public K getKey()   { return key; }
    public V getValue() { return value; }
}
```

>The complete syntax for invoking this method would be:
 ```java
Pair<Integer, String> p1 = new Pair<>(1, "apple");
Pair<Integer, String> p2 = new Pair<>(2, "pear");
boolean same = Util.<Integer, String>compare(p1, p2);
//or
boolean same = Util.compare(p1, p2);
```
### Bounded Type Parameters
> In addition to limiting the types you can use to instantiate a generic type, bounded type parameters allow you to invoke methods defined in the bounds:
- In bounded type you can extend generic type and add specific type with generics
- Here this example we can see generic type variable `T` have been extended by Integer
```java
public class NaturalNumber<T extends Integer> {

    private T n;

    public NaturalNumber(T n)  { this.n = n; }

    public boolean isEven() {
        return n.intValue() % 2 == 0;
    }

    // ...
}
```

### Multiple Bounds
> A type variable with multiple bounds is a subtype of all the types listed in the bound. If one of the bounds is a class, it must be specified first. For example:
```java
Class A { /* ... */ }
interface B { /* ... */ }
interface C { /* ... */ }

class D <T extends A & B & C> { /* ... */ }
```
> If bound A is not specified first, you get a compile-time error:
```java
class D <T extends B & A & C> { /* ... */ }  // compile-time error
```

### Generic Methods and Bounded Type Parameters
```java
public static <T> int countGreaterThan(T[] anArray, T elem) {
    int count = 0;
    for (T e : anArray)
        if (e > elem)  // compiler error
            ++count;
    return count;
}
```
> The implementation of the method is straightforward, but it does not compile because the greater than operator (>) applies only to primitive types such as short, int, double, long, float, byte, and char. You cannot use the > operator to compare objects. To fix the problem, use a type parameter bounded by the Comparable<T> interface:

```java
public interface Comparable<T> {
    public int compareTo(T o);
}

//Use bounded type parameters (<T extends Comparable<T>>) to ensure that T implements Comparable, allowing us to compare elements.
public static <T extends Comparable<T>> int countGreaterThan(T[] anArray, T elem) {
    int count = 0;
    for (T e : anArray)
        if (e.compareTo(elem) > 0)
            ++count;
    return count;
}

```

### Generics, Inheritance, and Subtypes

> As you already know, it is possible to assign an object of one type to an object of another type provided that the types are compatible. For example, you can assign an `Integer` to an `Object`, since `Object` is one of `Integer's` `supertypes`:
```java
Object someObject = new Object();
Integer someInteger = new Integer(10);
someObject = someInteger;   // OK as Integer supertype is Object
```