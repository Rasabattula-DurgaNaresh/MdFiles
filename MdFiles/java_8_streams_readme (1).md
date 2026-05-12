<a name="top"></a>
# Java 8 Streams Interview Prep 🚀

A structured collection of Java 8 Stream problems with solutions, difficulty levels, and collapsible sections for clean navigation.

---

## 📌 Navigation

- [Easy](#easy)
- [Medium](#medium)
- [Advanced](#advanced)

---

# 🟢 Easy
<a name="easy"></a>

<details>
<summary><b>1.1 Filter Even And Odd Numbers in a List (Easy)</b></summary>

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
</details>

---

<details>
<summary><b>1.2 Convert List Of String To Upper Case (Easy)</b></summary>

```java
List<String> names = Arrays.asList("a","b","c");

List<String> upper = names.stream()
    .map(String::toUpperCase)
    .toList();
```

[⬆ Back to Top](#top)
</details>

---

<details>
<summary><b>1.3 Sum Of All Numbers In A List (Easy)</b></summary>

```java
int sum = numbers.stream()
    .mapToInt(Integer::intValue)
    .sum();
```

[⬆ Back to Top](#top)
</details>

---

# 🟡 Medium
<a name="medium"></a>

<details>
<summary><b>1.9 Count Of Each Character In String (Medium)</b></summary>

```java
String str = "hello";

Map<Character, Long> map = str.chars()
    .mapToObj(c -> (char)c)
    .collect(Collectors.groupingBy(c -> c, Collectors.counting()));
```

[⬆ Back to Top](#top)
</details>

---

<details>
<summary><b>1.10 Count Of Each Word In String (Medium)</b></summary>

```java
String sentence = "hello world hello";

Map<String, Long> map = Arrays.stream(sentence.split(" "))
    .collect(Collectors.groupingBy(w -> w, Collectors.counting()));
```

[⬆ Back to Top](#top)
</details>

---

<details>
<summary><b>1.16 Partition Even Odd (Medium)</b></summary>

```java
Map<Boolean, List<Integer>> partitioned = numbers.stream()
    .collect(Collectors.partitioningBy(n -> n % 2 == 0));
```

[⬆ Back to Top](#top)
</details>

---

# 🔴 Advanced
<a name="advanced"></a>

<details>
<summary><b>1.17 Flatten List Of Lists (Advanced)</b></summary>

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
</details>

---

# 📁 Suggested Repository Structure

```
java-streams-interview/
│
├── README.md
├── src/
│   ├── easy/
│   │   ├── EvenOdd.java
│   │   ├── Uppercase.java
│   │
│   ├── medium/
│   │   ├── CharacterCount.java
│   │   ├── WordCount.java
│   │
│   ├── advanced/
│   │   ├── FlattenList.java
│
├── test/
│   ├── EasyTests.java
│   ├── MediumTests.java
│   ├── AdvancedTests.java
│
├── docs/
│   ├── stream-cheatsheet.md
│   ├── interview-questions.md
│
└── pom.xml / build.gradle
```

---

# 🔥 Bonus Ideas

- Add **JUnit tests** for each problem
- Add **time complexity explanations**
- Add **real interview questions section**
- Add **Java 17 enhancements (Stream.toList vs collect)**

---

💡 This format is optimized for GitHub readability + interview preparation.

