# Encapsulation in Depth

## 1. What is Encapsulation?

Encapsulation is a core Object-Oriented Programming (OOP) principle that:

* Bundles data and methods together
* Restricts direct access to internal state
* Exposes controlled interfaces

> "All interactions with data must go through well-defined rules."

---

## 2. Why Encapsulation Matters

### Data Protection

```java
class BankAccount {
    private double balance;

    public void deposit(double amount) {
        if (amount > 0) balance += amount;
    }
}
```

### Maintaining Invariants

* Prevent invalid states
* Example: balance should not be negative

### Loose Coupling

* External code depends only on public methods
* Internal implementation can change safely

### Supports Abstraction

* Hides "how"
* Exposes "what"

---

## 3. Levels of Encapsulation

### Weak

```java
class Student {
    public int age;
}
```

### Moderate

```java
class Student {
    private int age;

    public int getAge() { return age; }
    public void setAge(int age) {
        if (age > 0) this.age = age;
    }
}
```

### Strong (Best Practice)

```java
class BankAccount {
    private double balance;

    public void deposit(double amount) { }
    public void withdraw(double amount) { }
}
```

---

## 4. Encapsulation vs Data Hiding

| Concept       | Meaning                 |
| ------------- | ----------------------- |
| Encapsulation | Bundling data + methods |
| Data Hiding   | Restricting access      |

---

## 5. Interview Example

### Problem

Design a BankAccount class with safe operations

### Solution

```java
class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        if (initialBalance < 0) throw new IllegalArgumentException();
        this.balance = initialBalance;
    }

    public void deposit(double amount) {
        if (amount <= 0) throw new IllegalArgumentException();
        balance += amount;
    }

    public void withdraw(double amount) {
        if (amount <= 0 || amount > balance) throw new IllegalArgumentException();
        balance -= amount;
    }

    public double getBalance() {
        return balance;
    }
}
```

### Why No Setter?

```java
account.setBalance(-100000); // breaks rules
```

---

## 6. UML Diagram

```
+----------------------+
|    BankAccount       |
+----------------------+
| - balance: double    |
+----------------------+
| + deposit(amount)    |
| + withdraw(amount)   |
| + getBalance()       |
+----------------------+
```

---

## 7. Memory View (Stack vs Heap)

```
Stack                Heap
-----                ----------------
account  --------->  BankAccount
                     balance = 1000
```

---

## 8. Testing Encapsulation (JUnit)

### Valid Case

```java
@Test
public void testDeposit() {
    BankAccount acc = new BankAccount(1000);
    acc.deposit(500);
    assertEquals(1500, acc.getBalance());
}
```

### Invalid Case

```java
@Test(expected = IllegalArgumentException.class)
public void testInvalidDeposit() {
    BankAccount acc = new BankAccount(1000);
    acc.deposit(-100);
}
```

---

## 9. Common Mistakes

* Public fields
* No validation
* Overuse of setters
* Breaking encapsulation

---

## 10. Advanced Concepts

### Immutability

```java
final class Person {
    private final String name;

    public Person(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```

### API Design

* Minimal exposure
* Safe operations only

---

## 11. Real-World Examples

* ATM machines
* Payment systems
* E-commerce checkout

---

## 12. Key Takeaways

* Control access
* Protect data
* Maintain invariants
* Expose behavior, not state

---

## 13. Learning Progression

| Level        | Focus                  |
| ------------ | ---------------------- |
| Beginner     | Getters/Setters        |
| Intermediate | Validation             |
| Advanced     | Behavior-driven design |
| Expert       | Domain-driven design   |

---

## Conclusion

Encapsulation is not just about hiding data. It is about designing systems that are:

* Safe
* Maintainable
* Scalable
* Robust
