## 01) Given a list of strings, write a program to remove duplicates using Stream API while maintaining insertion order.

### Code

```java
import java.util.*;
import java.util.stream.*;

public class StreamAPIExample
{
	public static void main(String[] args) {
		List<String> l1 = Arrays.asList("Apple","Mango","Banana","Grapes","Mango","BlueBerrys","Apple");

		//Remove Duplicate from list and maintain the insertion order
		List<String> res = l1.stream().distinct().collect(Collectors.toList());
		System.out.println(res);

		//Inline Print
		l1.stream().distinct().forEach(System.out::println);
	}
}
```

### Output
```
[Apple, Mango, Banana, Grapes, BlueBerrys]
Apple
Mango
Banana
Grapes
BlueBerrys
```
---

## 02) Given a list of integers, write a program to find numbers that start with 1 using Stream API.

### Code

```java
import java.util.*;
import java.util.stream.*;

public class StreamAPIExample
{
	public static void main(String[] args) {
		
		List<Integer> numbers = Arrays.asList(10,20,31,12,90,67,11,100,36);
		
		//print numbers which start with 1
		//Now in number we don't have any function to get first so we need to convert that to String
		List<Integer> startsWithOne = numbers.stream()
		    .filter(num -> String.valueOf(num).startsWith("1"))
		    .collect(Collectors.toList());
		    
		System.out.println(startsWithOne);
		
		//print numbers which do not start with 1
		List<Integer> notStartsWithOne = numbers.stream()
		    .filter(num -> !String.valueOf(num).startsWith("1"))
		    .collect(Collectors.toList());
		
		System.out.println(notStartsWithOne);
	}
}
```

### Output
```
[10, 12, 11, 100]
[20, 31, 90, 67, 36]
```
---

## 03) Given two lists of integers, write a program to merge them into a single list using Stream API.

### Code

```java
import java.util.*;
import java.util.stream.*;

public class StreamAPIExample
{
	public static void main(String[] args) {
		
		List<Integer> l1 = Arrays.asList(10,20,31,12,90,67,11,04,36);
		List<Integer> l2 = Arrays.asList(01,22,14,62,80,77,16,10,60);
		
		//Merge 2 stream into single stream
		List<Integer> res = Stream.concat(l1.stream(), l2.stream())
		                          .collect(Collectors.toList());
		
		System.out.println(res);
	}
}
```

### Output
```
[10, 20, 31, 12, 90, 67, 11, 4, 36, 1, 22, 14, 62, 80, 77, 16, 10, 60]
```
---

## 04) Given two sorted lists of integers, write a program to merge them into a single sorted list using Stream API.

### Code

```java
import java.util.*;
import java.util.stream.*;

public class StreamAPIExample
{
	public static void main(String[] args) {
		
		List<Integer> l1 = Arrays.asList(10,20,31,32,30,77);
		List<Integer> l2 = Arrays.asList(47,51,52,54,62,70);
		
		//Merge 2 sorted list into single sorted list using stream
		List<Integer> mergedList = Stream.concat(l1.stream(), l2.stream())
		                                 .sorted()
		                                 .collect(Collectors.toList());
		
		System.out.println(mergedList);
	}
}
```

### Output
```
[10, 20, 30, 31, 32, 47, 51, 52, 54, 62, 70, 77]
```
---

## 05) Given a list of integers, write a program to check if it contains any prime numbers using Stream API, and print them if present.

### Code

```java
import java.util.*;
import java.util.stream.*;

public class StreamAPIExample
{
	public static void main(String[] args) {

		List<Integer> l1 = Arrays.asList(10,20,31,32,30,77);

		//Check if the list contains prime numbers or not
		boolean containsPrime = l1.stream().anyMatch(f -> isPrime(f));
		System.out.println("List Contains Prime No :" + containsPrime);

		//Print values if the list contains prime numbers
		List<Integer> listOfprimeNo = l1.stream()
		                                .filter(f -> isPrime(f))
		                                .collect(Collectors.toList());
		System.out.println(listOfprimeNo);
	}

	public static boolean isPrime(int num) {
		if (num <= 1) return false;

		for (int i = 2; i <= num / 2; i++) {
			if (num % i == 0) {
				return false;
			}
		}
		return true;
	}
}
```

### Output
```
List Contains Prime No : true
[31]
```
---
