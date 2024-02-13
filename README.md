# JavaSE-Iterable and Collections

See the Udemy course: https://www.udemy.com/course/curso-certificacion-profesional-desarrollador-java-se-11

In Java, "Iterable" and "Collections" are both related to handling collections of objects, but they serve slightly different purposes.

## Iterable (java.util.Iterator)

The Iterable interface is a part of the Java Collections Framework and represents a sequence of elements that can be iterated (looped) sequentially. 

It doesn't provide methods to directly access elements; instead, it has one method - iterator(). 

The iterator() method returns an Iterator object that allows you to iterate through the elements of the collection.

```java
import java.util.Iterator;

public class MyIterableCollection implements Iterable<String> {
    private String[] elements;

    public MyIterableCollection(String[] elements) {
        this.elements = elements;
    }

    @Override
    public Iterator<String> iterator() {
        return new Iterator<String>() {
            private int index = 0;

            @Override
            public boolean hasNext() {
                return index < elements.length;
            }

            @Override
            public String next() {
                return elements[index++];
            }
        };
    }

    public static void main(String[] args) {
        String[] data = {"Apple", "Banana", "Orange"};
        MyIterableCollection collection = new MyIterableCollection(data);

        for (String element : collection) {
            System.out.println(element);
        }
    }
}
```

## Collections (java.util.Collections)

On the other hand, the Collections class is a utility class in Java that consists of static methods that operate on or return collections. 

It provides methods for searching, sorting, and manipulating collections.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class CollectionsExample {
    public static void main(String[] args) {
        List<String> myList = new ArrayList<>();
        myList.add("Apple");
        myList.add("Banana");
        myList.add("Orange");

        // Sorting the list
        Collections.sort(myList);

        // Printing the sorted list
        for (String element : myList) {
            System.out.println(element);
        }
    }
}
```

In this example, Collections.sort() is used to sort the list in natural order.

In summary, Iterable is an interface that allows an object to be the target of the "foreach" statement, 

while Collections is a utility class with static methods for various operations on collections.
