# Java 8 Collectors – Complete Guide

## 1. Stream.collect()
- Terminal operation
- Used for mutable reduction
- Uses `Collector` interface

---

## 2. toList()
```java
List<String> names = employeeList.stream()
    .map(Employee::getName)
    .collect(Collectors.toList());
```
- No guarantee on type or mutability

---

## 3. toSet()
```java
Set<String> regions = employeeList.stream()
    .map(Employee::getRegion)
    .collect(Collectors.toSet());
```

---

## 4. toUnmodifiableSet()
- Immutable
- Throws exception on modification
- No null allowed

---

## 5. toUnmodifiableList()
- Immutable list
- Allows duplicates
- No null allowed

---

## 6. toCollection()
```java
List<String> list = employeeList.stream()
    .map(Employee::getName)
    .collect(Collectors.toCollection(LinkedList::new));
```

---

## 7. toMap()
```java
Map<Integer, Employee> map =
    employeeList.stream().collect(
        Collectors.toMap(e -> e.getId(), Function.identity()));
```

### Duplicate Key Handling
```java
Collectors.toMap(
    e -> e.getId(),
    Function.identity(),
    (oldVal, newVal) -> newVal
)
```

---

## 8. toUnmodifiableMap()
- Immutable map

---

## 9. summingInt / summingDouble
```java
int sum = employeeList.stream()
    .collect(Collectors.summingInt(Employee::getId));
```

---

## 10. averagingDouble
```java
double avg = employeeList.stream()
    .collect(Collectors.averagingDouble(Employee::getSal));
```

---

## 11. counting()
```java
long count = employeeList.stream()
    .collect(Collectors.counting());
```

---

## 12. joining()
```java
String names = employeeList.stream()
    .map(Employee::getName)
    .collect(Collectors.joining(", "));
```

---

## 13. groupingBy()
```java
Map<String, List<Employee>> grouped =
    employeeList.stream()
        .collect(Collectors.groupingBy(Employee::getRegion));
```

---

## 14. partitioningBy()
```java
Map<Boolean, List<Employee>> result =
    employeeList.stream()
        .collect(Collectors.partitioningBy(e -> e.getAge() > 30));
```

---

## 15. toConcurrentMap()
```java
ConcurrentMap<Integer, Employee> map =
    employeeList.stream().collect(
        Collectors.toConcurrentMap(e -> e.getId(), Function.identity()));
```

---

## 16. filtering()
```java
List<Employee> filtered =
    employeeList.stream().collect(
        Collectors.filtering(e -> e.getAge() > 30, Collectors.toList()));
```

---

## 17. flatMapping()
```java
Map<String, Set<LineItem>> result =
    customers.stream().collect(
        Collectors.groupingBy(Customer::getGender,
            Collectors.flatMapping(c -> c.getLineItems().stream(),
                Collectors.toSet())));
```

---

## 18. maxBy / minBy
```java
Optional<Employee> max =
    employeeList.stream().collect(
        Collectors.maxBy(Comparator.comparing(Employee::getId)));
```

---

## 19. reducing()
```java
Optional<Employee> min =
    employeeList.stream().collect(
        Collectors.reducing(BinaryOperator.minBy(
            Comparator.comparing(Employee::getId))));
```

---

## 20. summarizingDouble()
```java
DoubleSummaryStatistics stats =
    employeeList.stream()
        .collect(Collectors.summarizingDouble(Employee::getSal));
```

---

## 21. teeing() (Java 12)
```java
double avg = list.stream().collect(
    Collectors.teeing(
        Collectors.summingDouble(i -> i),
        Collectors.counting(),
        (sum, count) -> sum / count));
```

---

## Tips
- Prefer `groupingBy` over manual loops
- Handle duplicates in `toMap`
- Use `toCollection` for specific implementations
- Use `teeing` for combined calculations

---

## Edge Cases
- Nulls not allowed in unmodifiable collectors
- Duplicate keys crash `toMap`
- TreeSet requires Comparable

---

## End of File
