<a name="top"></a>
# Java 8 Streams Basic Coding Questions

A collection of common Java 8 Stream problems with solutions.

---

## 📌 Navigation

- [1.1 Filter Even And Odd Numbers in a List](#11-filter-even-and-odd-numbers-in-a-list)
- [1.2 Convert List Of String To Upper Case](#12-convert-list-of-string-to-upper-case)
- [1.3 Sum Of All Numbers In A List](#13-sum-of-all-numbers-in-a-list)
- [1.4 Find Maximum Number In A List](#14-find-maximum-number-in-a-list)
- [1.5 Sort List Of Integers](#15-sort-list-of-integers)
- [1.6 Remove Duplicates In A List](#16-remove-duplicates-in-a-list)
- [1.7 Count No Of Elements In List](#17-count-no-of-elements-in-list)
- [1.8 Matching Functions](#18-matching-functions)
- [1.9 Count Of Each Character In String](#19-count-of-each-character-in-string)
- [1.10 Count Of Each Word In String](#110-count-of-each-word-in-string)
- [1.11 Count Strings Longer Than Five](#111-count-strings-longer-than-five)
- [1.12 Sum Numbers Greater Than Ten](#112-sum-numbers-greater-than-ten)
- [1.13 Find First Divisible By Seven](#113-find-first-divisible-by-seven)
- [1.14 List To Map Word Length](#114-list-to-map-word-length)
- [1.15 GroupBy FirstLetter](#115-groupby-firstletter)
- [1.16 Partition Even Odd](#116-partition-even-odd)
- [1.17 Flatten List Of Lists](#117-flatten-list-of-lists)
- [1.18 Print First Element](#118-print-first-element)
- [1.19 Optional Find String Starting With A](#119-optional-find-string-starting-with-a)

---

## 1.1 Filter Even And Odd Numbers in a List
```java
List<Integer> numbers = Arrays.asList(1,2,3,4,5,6);

List<Integer> evens = numbers.stream()
    .filter(n -> n % 2 == 0)
    .toList();

List<Integer> odds = numbers.stream()
    .filter(n -> n % 2 != 0)
    .toList();
```

[⬆ Back to Top](#top)

---

## 1.2 Convert List Of String To Upper Case
```java
List<String> names = Arrays.asList("a","b","c");

List<String> upper = names.stream()
    .map(String::toUpperCase)
    .toList();
```

[⬆ Back to Top](#top)

---

## 1.3 Sum Of All Numbers In A List
```java
int sum = numbers.stream()
    .mapToInt(Integer::intValue)
    .sum();
```

[⬆ Back to Top](#top)

---

## 1.4 Find Maximum Number In A List
```java
Optional<Integer> max = numbers.stream()
    .max(Integer::compareTo);
```

[⬆ Back to Top](#top)

---

## 1.5 Sort List Of Integers
```java
List<Integer> sorted = numbers.stream()
    .sorted()
    .toList();
```

[⬆ Back to Top](#top)

---

## 1.6 Remove Duplicates In A List
```java
List<Integer> unique = numbers.stream()
    .distinct()
    .toList();
```

[⬆ Back to Top](#top)

---

## 1.7 Count No Of Elements In List
```java
long count = numbers.stream().count();
```

[⬆ Back to Top](#top)

---

## 1.8 Matching Functions
```java
boolean allMatch = numbers.stream().allMatch(n -> n > 0);
boolean anyMatch = numbers.stream().anyMatch(n -> n > 5);
boolean noneMatch = numbers.stream().noneMatch(n -> n < 0);
```

[⬆ Back to Top](#top)

---

## 1.9 Count Of Each Character In String
```java
String str = "hello";

Map<Character, Long> map = str.chars()
    .mapToObj(c -> (char)c)
    .collect(Collectors.groupingBy(c -> c, Collectors.counting()));
```

[⬆ Back to Top](#top)

---

## 1.10 Count Of Each Word In String
```java
String sentence = "hello world hello";

Map<String, Long> map = Arrays.stream(sentence.split(" "))
    .collect(Collectors.groupingBy(w -> w, Collectors.counting()));
```

[⬆ Back to Top](#top)

---

## 1.11 Count Strings Longer Than Five
```java
long count = names.stream()
    .filter(s -> s.length() > 5)
    .count();
```

[⬆ Back to Top](#top)

---

## 1.12 Sum Numbers Greater Than Ten
```java
int sum = numbers.stream()
    .filter(n -> n > 10)
    .mapToInt(Integer::intValue)
    .sum();
```

[⬆ Back to Top](#top)

---

## 1.13 Find First Divisible By Seven
```java
Optional<Integer> result = numbers.stream()
    .filter(n -> n % 7 == 0)
    .findFirst();
```

[⬆ Back to Top](#top)

---

## 1.14 List To Map Word Length
```java
Map<String, Integer> map = names.stream()
    .collect(Collectors.toMap(
        s -> s,
        s -> s.length()
    ));
```

[⬆ Back to Top](#top)

---

## 1.15 GroupBy FirstLetter
```java
Map<Character, List<String>> grouped = names.stream()
    .collect(Collectors.groupingBy(s -> s.charAt(0)));
```

[⬆ Back to Top](#top)

---

## 1.16 Partition Even Odd
```java
Map<Boolean, List<Integer>> partitioned = numbers.stream()
    .collect(Collectors.partitioningBy(n -> n % 2 == 0));
```

[⬆ Back to Top](#top)

---

## 1.17 Flatten List Of Lists
```java
List<List<Integer>> list = Arrays.asList(
    Arrays.asList(1,2),
    Arrays.asList(3,4)
);

List<Integer> flat = list.stream()
    .flatMap(Collection::stream)
    .toList();
```

[⬆ Back to Top](#top)

---

## 1.18 Print First Element
```java
numbers.stream()
    .findFirst()
    .ifPresent(System.out::println);
```

[⬆ Back to Top](#top)

---

## 1.19 Optional Find String Starting With A
```java
Optional<String> result = names.stream()
    .filter(s -> s.startsWith("A"))
    .findFirst();
```

[⬆ Back to Top](#top)

