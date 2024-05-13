## Java 8 Features

### Stream API

- Stream API is related to the collection framework (Group Of Objects).
- These are used to process a group of objects.
- This was introduced in Java 1.8 version.
- It performs bulk operations and processes the objects of collections.
- It reduces the length of code.

By using 2 ways we will see the difference between using stream and without stream
## Without Using Stream
```java
// Without Stream
List<Integer> l1 = new ArrayList<>();
l1.add(2);
l1.add(3);
l1.add(5);
l1.add(7);
l1.add(12);
l1.add(14);
l1.add(23);
l1.add(45);
l1.add(50);
System.out.println(l1);

List listEvn = new ArrayList<>();

for (Integer i: l1) {
    if (i % 2 == 0){
        listEvn.add(i);
    }
}
System.out.println(listEvn);
```

Output:
```
[2, 3, 5, 7, 12, 14, 23, 45, 50]
[2, 12, 14, 50]
```

## Using Stream

```java
List<Integer> l1 = new ArrayList<>();
l1.add(2);
l1.add(3);
l1.add(5);
l1.add(7);
l1.add(12);
l1.add(14);
l1.add(23);
l1.add(45);
l1.add(50);
System.out.println(l1);

Stream<Integer> stream = l1.stream();
List<Integer> filteredList = stream.filter(i -> i % 2 == 0).collect(Collectors.toList());
System.out.println(filteredList);
```

Output:
```
[2, 3, 5, 7, 12, 14, 23, 45, 50]
[2, 12, 14, 50]
```

So here we have achieved the same functionality with less code. We created a stream and used the `filter` method with a lambda expression to filter the list using the Stream API.

## Methods In Stream API

There are various methods in the Stream API. A few are as follows:

### Filters

```java
// filter(predicates) 
// Basically predicates are boolean value functions, which means that it takes an expression as a boolean value function.
// Eg:
// filter(i -> i % 2 == 0)
```

// In that example, the `i % 2 == 0` expression returns a true or false value. If it's true, then it will be collected, otherwise, it will be ignored.

### Map

```java
// map(function)
// By using `map()`, we can perform operations on each element.
```


Eg:-

```java
package work;

import java.util.List;
import java.util.stream.Collectors;

public class Methods {

    public static void main(String[] args) {
        System.out.println("Methods in Stream API");
        
        // Filters
        List<String> cities = List.of("Pune", "Mumbai", "Hyderabad", "Delhi", "Chennai", "Bangalore");
        List<String> filteredList = cities.stream().filter(i -> i.startsWith("P")).collect(Collectors.toList());
        System.out.println(filteredList);

        // Map
        List<Integer> nums = List.of(2, 4, 5, 7, 8);
        List<Integer> result = nums.stream().map(e -> e * e).collect(Collectors.toList());
        System.out.println(result);

        // ForEach
        List<String> technologies = List.of("Java", "JavaScript", "Python", "Spring", "DataStructure");
        technologies.stream().forEach(e -> {
            System.out.println(e);
        });
    }
}
```
