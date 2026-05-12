# <b> Is Java Pass-by-Value or Pass-by-Reference? </b>

# Introduction
   One of the most common questions when learning Java is whether Java uses pass-by-value or pass-by-reference when passing arguments to methods. There is a lot of confusion around this, especially when it comes to how Java handles objects. In this blog, we’ll clear up the confusion with simple explanations and examples so you can easily understand how Java works.

# What Does Pass-by-Value and Pass-by-Reference Mean?
   Pass-by-value: When you pass a value to a method, a copy of that value is made. If the method changes the value, the original value remains unchanged.

# Pass-by-reference: 
  When you pass by reference, the method gets a reference (or memory address) to the original object or value. If the method changes it, the original value is affected.

  Now, let’s see how Java handles these situations.

# Is Java Pass-by-Value or Pass-by-Reference?
  Java is strictly pass-by-value. This means whenever you pass something to a method, Java creates a copy of that value, and the method works with the copy.

  But what about objects? When it comes to objects, Java passes a copy of the reference (memory location) to the object. This often makes it look like a pass-by-reference, but it's still a pass-by-value of the reference.

# Let's look at examples to make this clear.

    Example 1: Passing Primitive Data Types
    Let’s first look at how Java handles basic data types like int, char, or double.

```java
public class PrimitiveExample {
    public static void main(String[] args) {
        int number = 10;
        modifyPrimitive(number);
        System.out.println("Number after method call: " + number);
    }

    public static void modifyPrimitive(int value) {
        value = 20;  // Changes the local copy, not the original 'number'
    }
}

Output:
Number after method call: 10
```

# Explanation:
  In this example:

  The method modifyPrimitive() changes the value of value to 20, but this only affects the local copy inside the method.
  The original number variable in the main() method remains unchanged.
  This clearly shows that Java passes primitive types by value—the method only gets a copy of the value.

# Example 2: Passing Objects
  Now, let’s see what happens when we pass an object to a method.

```java 
class Person {
    String name;
}

public class ObjectExample {
    public static void main(String[] args) {
        Person person = new Person();
        person.name = "John";

        modifyObject(person);
        System.out.println("Person's name after method call: " + person.name);
    }

    public static void modifyObject(Person p) {
        p.name = "Mike";  // Changes the 'name' property of the original object
    }
}
Output:
Person's name after method call: Mike
```
# Explanation:
  In this case:

  The method modifyObject() changes the name property of the Person object.
  Even though Java passes a copy of the reference to the object, the method still changes the name because both the original and the copy refer to the same object in memory.
  This might seem like a pass-by-reference, but remember: Java passes a copy of the reference, not the object itself.

# Example 3: Reassigning Object References
  Let’s see what happens when we try to change the object reference itself inside a method.

```java
class Person {
    String name;
}

public class ReferenceExample {
    public static void main(String[] args) {
        Person person = new Person();
        person.name = "John";

        reassignReference(person);
        System.out.println("Person's name after reassignment attempt: " + person.name);
    }

    public static void reassignReference(Person p) {
        p = new Person();  // Reassigns the local reference to a new object
        p.name = "Mike";
    }
}
Output:
Person's name after reassignment attempt: John
```
# Explanation:
  Inside the method reassignReference(), we create a new Person object and assign it to p, but this does not affect the original person object in the main() method.
  After the method call, the original object still has the name "John" because reassigning the local reference inside the method does not change the original reference.
  This proves that Java passes object references by value, and the reference itself cannot be reassigned to affect the original object outside the method.

# Conclusion
  To sum it up:

# Java is pass-by-value.
  When you pass a primitive type to a method, the method works on a copy of the value, so the original value remains unchanged.
  When you pass an object, Java passes a copy of the reference to the object. While the method can modify the object’s properties, it cannot change the reference itself.
  So, Java always passes by value, but when it comes to objects, it’s the reference that is passed by value. This sometimes makes it look like a pass-by-reference, but it’s not.   