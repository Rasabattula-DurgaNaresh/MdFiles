    # Java 8 Stream – 100 Coding Questions with Solutions

## 1. Convert List of Strings to Uppercase
```java
List<String> result = list.stream()
        .map(String::toUpperCase)
        .collect(Collectors.toList());
```

## 2. Convert List of Strings to Lowercase
```java
list.stream().map(String::toLowerCase).collect(Collectors.toList());
```

## 3. Find Length of Each String
```java
list.stream().map(String::length).collect(Collectors.toList());
```

## 4. Filter Even Numbers
```java
list.stream().filter(n -> n % 2 == 0).collect(Collectors.toList());
```

## 5. Filter Odd Numbers
```java
list.stream().filter(n -> n % 2 != 0).collect(Collectors.toList());
```

## 6. Numbers Greater Than 10
```java
list.stream().filter(n -> n > 10).collect(Collectors.toList());
```

## 7. Count Elements
```java
long count = list.stream().count();
```

## 8. Sort Ascending
```java
list.stream().sorted().collect(Collectors.toList());
```

## 9. Sort Descending
```java
list.stream().sorted(Comparator.reverseOrder()).collect(Collectors.toList());
```

## 10. Remove Duplicates
```java
list.stream().distinct().collect(Collectors.toList());
```

## 11. Get First Element
```java
Optional<Integer> first = list.stream().findFirst();
```

## 12. Skip First 3 Elements
```java
list.stream().skip(3).collect(Collectors.toList());
```

## 13. Limit First 5 Elements
```java
list.stream().limit(5).collect(Collectors.toList());
```

## 14. Any Number > 50
```java
boolean result = list.stream().anyMatch(n -> n > 50);
```

## 15. All Numbers Positive
```java
boolean result = list.stream().allMatch(n -> n > 0);
```

## 16. None Negative
```java
boolean result = list.stream().noneMatch(n -> n < 0);
```

## 17. Maximum Number
```java
Optional<Integer> max = list.stream().max(Integer::compare);
```

## 18. Minimum Number
```java
Optional<Integer> min = list.stream().min(Integer::compare);
```

## 19. List<Integer> → List<String>
```java
list.stream().map(String::valueOf).collect(Collectors.toList());
```

## 20. Multiply Each Number by 2
```java
list.stream().map(n -> n * 2).collect(Collectors.toList());
```

## 21. Square Each Number
```java
list.stream().map(n -> n * n).collect(Collectors.toList());
```

## 22. Strings Starting With A
```java
list.stream().filter(s -> s.startsWith("A")).collect(Collectors.toList());
```

## 23. Strings Ending With n
```java
list.stream().filter(s -> s.endsWith("n")).collect(Collectors.toList());
```

## 24. Sum of Numbers
```java
int sum = list.stream().mapToInt(Integer::intValue).sum();
```

## 25. Average of Numbers
```java
double avg = list.stream().mapToInt(Integer::intValue).average().orElse(0);
```

---

# Intermediate Problems

## 26. Second Highest Number
```java
Integer second = list.stream()
        .sorted(Comparator.reverseOrder())
        .skip(1)
        .findFirst().get();
```

## 27. Second Smallest
```java
Integer second = list.stream()
        .sorted()
        .skip(1)
        .findFirst().get();
```

## 28. Find Duplicates
```java
Set<Integer> set = new HashSet<>();
list.stream().filter(n -> !set.add(n)).collect(Collectors.toSet());
```

## 29. Unique Elements
```java
list.stream().distinct().collect(Collectors.toList());
```

## 30. Count Occurrence of Each Element
```java
Map<Integer, Long> map =
        list.stream().collect(Collectors.groupingBy(e -> e, Collectors.counting()));
```

## 31. Character Frequency in String
```java
Map<Character, Long> map =
        str.chars()
           .mapToObj(c -> (char)c)
           .collect(Collectors.groupingBy(c -> c, Collectors.counting()));
```

## 32. First Non-Repeating Character
```java
Character c = str.chars()
        .mapToObj(x -> (char)x)
        .collect(Collectors.groupingBy(e -> e, LinkedHashMap::new, Collectors.counting()))
        .entrySet().stream()
        .filter(e -> e.getValue() == 1)
        .findFirst().get().getKey();
```

## 33. Reverse String
```java
String reversed =
        IntStream.range(0, str.length())
                 .mapToObj(i -> str.charAt(str.length()-1-i))
                 .map(String::valueOf)
                 .collect(Collectors.joining());
```

## 34. Longest String
```java
String longest =
        list.stream().max(Comparator.comparing(String::length)).get();
```

## 35. Shortest String
```java
String shortest =
        list.stream().min(Comparator.comparing(String::length)).get();
```

## 36. Join Strings
```java
String result = list.stream().collect(Collectors.joining(","));
```

## 37. Group Strings by Length
```java
Map<Integer,List<String>> map =
        list.stream().collect(Collectors.groupingBy(String::length));
```

## 38. Partition Even and Odd
```java
Map<Boolean,List<Integer>> map =
        list.stream().collect(Collectors.partitioningBy(n -> n % 2 == 0));
```

## 39. Top 3 Highest Numbers
```java
list.stream().sorted(Comparator.reverseOrder()).limit(3).collect(Collectors.toList());
```

## 40. Bottom 3 Numbers
```java
list.stream().sorted().limit(3).collect(Collectors.toList());
```

---

# Advanced Problems

## 41. Flatten List<List<Integer>>
```java
list.stream().flatMap(Collection::stream).collect(Collectors.toList());
```

## 42. Remove Null Values
```java
list.stream().filter(Objects::nonNull).collect(Collectors.toList());
```

## 43. Common Elements Between Two Lists
```java
list1.stream().filter(list2::contains).collect(Collectors.toList());
```

## 44. Merge Two Lists
```java
Stream.concat(list1.stream(), list2.stream())
      .collect(Collectors.toList());
```

## 45. Check Palindrome Strings
```java
list.stream()
    .filter(s -> s.equals(new StringBuilder(s).reverse().toString()))
    .collect(Collectors.toList());
```

## 46. Count Words in Sentence
```java
long count = Arrays.stream(sentence.split(" ")).count();
```

## 47. Longest Word
```java
Arrays.stream(sentence.split(" "))
      .max(Comparator.comparing(String::length)).get();
```

## 48. Distinct Characters
```java
str.chars().mapToObj(c -> (char)c).distinct().collect(Collectors.toList());
```

## 49. Factorial Using Streams
```java
int factorial = IntStream.rangeClosed(1,n).reduce(1,(a,b)->a*b);
```

## 50. Fibonacci Using Streams
```java
Stream.iterate(new int[]{0,1},f->new int[]{f[1],f[0]+f[1]})
      .limit(10)
      .map(f->f[0])
      .forEach(System.out::println);
```

# Java 8 Stream Real-Time Interview Problems

This document contains **real-time Java 8 Stream coding interview problems with solutions** frequently asked in software interviews.

---

# 1. Find Duplicate Elements in a List

### Problem
Find duplicate numbers from a list using Java 8 streams.

### Solution
```java
List<Integer> list = Arrays.asList(1,2,3,4,2,5,3,6);

Set<Integer> set = new HashSet<>();

Set<Integer> duplicates = list.stream()
        .filter(n -> !set.add(n))
        .collect(Collectors.toSet());

System.out.println(duplicates);
```

---

# 2. Find First Non-Repeating Character in a String

### Problem
Return the first character that does not repeat in a string.

### Solution
```java
String str = "javaarticles";

Character result = str.chars()
        .mapToObj(c -> (char)c)
        .collect(Collectors.groupingBy(c -> c,
                LinkedHashMap::new,
                Collectors.counting()))
        .entrySet()
        .stream()
        .filter(e -> e.getValue() == 1)
        .findFirst()
        .get()
        .getKey();

System.out.println(result);
```

---

# 3. Find Second Highest Number in a List

### Problem
Find the second highest number using streams.

### Solution
```java
List<Integer> list = Arrays.asList(10,20,30,40,50);

Integer secondHighest = list.stream()
        .sorted(Comparator.reverseOrder())
        .skip(1)
        .findFirst()
        .get();

System.out.println(secondHighest);
```

---

# 4. Find Employee with Highest Salary

### Employee Class
```java
class Employee {
    int id;
    String name;
    double salary;

    // constructor + getters
}
```

### Solution
```java
Employee emp = employees.stream()
        .max(Comparator.comparing(Employee::getSalary))
        .get();
```

---

# 5. Group Employees by Department

### Problem
Group employees by department.

### Solution
```java
Map<String, List<Employee>> map =
        employees.stream()
                .collect(Collectors.groupingBy(Employee::getDepartment));
```

---

# 6. Count Occurrence of Each Word

### Problem
Count word frequency in a sentence.

### Solution
```java
String sentence = "java is great and java is powerful";

Map<String, Long> map =
        Arrays.stream(sentence.split(" "))
                .collect(Collectors.groupingBy(
                        word -> word,
                        Collectors.counting()
                ));
```

---

# 7. Remove Duplicate Elements

### Problem
Remove duplicates from a list.

### Solution
```java
List<Integer> result =
        list.stream()
            .distinct()
            .collect(Collectors.toList());
```

---

# 8. Find Even Numbers

### Problem
Filter even numbers using streams.

### Solution
```java
List<Integer> result =
        list.stream()
            .filter(n -> n % 2 == 0)
            .collect(Collectors.toList());
```

---

# 9. Find Common Elements Between Two Lists

### Problem
Find intersection of two lists.

### Solution
```java
List<Integer> common =
        list1.stream()
             .filter(list2::contains)
             .collect(Collectors.toList());
```

---

# 10. Find Longest String in List

### Solution
```java
String longest =
        list.stream()
            .max(Comparator.comparing(String::length))
            .get();
```

---

# 11. Find Palindrome Strings in List

### Solution
```java
List<String> result =
        list.stream()
            .filter(s -> s.equals(new StringBuilder(s).reverse().toString()))
            .collect(Collectors.toList());
```

---

# 12. Convert List to Map

### Problem
Convert list of employees to map using id.

### Solution
```java
Map<Integer, Employee> map =
        employees.stream()
                .collect(Collectors.toMap(
                        Employee::getId,
                        e -> e
                ));
```

---

# 13. Find Average Salary of Employees

### Solution
```java
double avgSalary =
        employees.stream()
                .collect(Collectors.averagingDouble(Employee::getSalary));
```

---

# 14. Partition Numbers into Even and Odd

### Solution
```java
Map<Boolean, List<Integer>> map =
        list.stream()
            .collect(Collectors.partitioningBy(n -> n % 2 == 0));
```

---

# 15. Find Top 3 Highest Numbers

### Solution
```java
List<Integer> result =
        list.stream()
            .sorted(Comparator.reverseOrder())
            .limit(3)
            .collect(Collectors.toList());
```

---

# 16. Flatten List of Lists

### Solution
```java
List<Integer> flat =
        listOfLists.stream()
                .flatMap(Collection::stream)
                .collect(Collectors.toList());
```

---

# 17. Count Characters in String

### Solution
```java
Map<Character, Long> map =
        str.chars()
            .mapToObj(c -> (char)c)
            .collect(Collectors.groupingBy(
                    c -> c,
                    Collectors.counting()
            ));
```

---

# 18. Sort Employees by Salary

### Solution
```java
List<Employee> sorted =
        employees.stream()
                .sorted(Comparator.comparing(Employee::getSalary))
                .collect(Collectors.toList());
```

---

# 19. Find Employee with Second Highest Salary

### Solution
```java
Employee emp =
        employees.stream()
                .sorted(Comparator.comparing(Employee::getSalary).reversed())
                .skip(1)
                .findFirst()
                .get();
```

---

# 20. Generate Fibonacci Using Streams

### Solution
```java
Stream.iterate(new int[]{0,1},
        f -> new int[]{f[1], f[0] + f[1]})
        .limit(10)
        .map(f -> f[0])
        .forEach(System.out::println);
```

---

# 21–30 Practice Problems

21. Find kth largest element  
22. Find employees hired last year  
23. Find department with highest salary  
24. Count employees per department  
25. Remove null values from list  
26. Find most frequent element  
27. Find least frequent element  
28. Sort map by value  
29. Find duplicate employees by id  
30. Merge two maps using streams

---

# Tips for Interviews

1. Understand **map, filter, reduce**
2. Practice **groupingBy**
3. Practice **partitioningBy**
4. Learn **flatMap**
5. Understand **Optional**
6. Use **Comparator with streams**

---

# End
These problems are commonly asked in **Java backend developer interviews**.
Practice them regularly to master **Java 8 Streams**.

---

# More Practice (51–100)
Practice similar problems using Streams:

51. kth largest element  
52. employee grouping by department  
53. employee max salary  
54. average salary by department  
55. sort employees by age  
56. employee hired in last year  
57. remove duplicate employees by id  
58. intersection of multiple lists  
59. union of lists  
60. difference of lists  
61. count vowels in string  
62. most frequent character  
63. least frequent character  
64. group words by first letter  
65. sort map by value  
66. sort map by key  
67. convert list to map  
68. map keys to list  
69. flatten nested objects  
70. filter null objects  
71. collect to set  
72. collect to linked list  
73. group numbers by remainder  
74. partition primes  
75. find primes  
76. running sum  
77. cumulative multiplication  
78. median calculation  
79. top frequent numbers  
80. bottom frequent numbers  
81. sliding window average  
82. custom collector  
83. grouping multiple fields  
84. nested grouping  
85. flatten employee skills  
86. stream pagination  
87. CSV parsing  
88. reading files with streams  
89. parallel stream sum  
90. performance comparison  
91. grouping by month  
92. find duplicates across lists  
93. sort by multiple fields  
94. mapping DTO objects  
95. reduce to map  
96. merge maps  
97. aggregate statistics  
98. percentile calculation  
99. batch processing with streams  
100. streaming large dataset

---

# End
These 100 problems cover **beginner → advanced Java 8 Stream interview preparation**.