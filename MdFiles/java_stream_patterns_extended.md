# Java 8 Stream-Based Pattern Problems (Extended)

## 🔥 1. Diamond Pattern

``` java
int n = 4;
IntStream.rangeClosed(1, n)
        .forEach(i -> System.out.println(" ".repeat(n - i) + "*".repeat(2 * i - 1)));

IntStream.iterate(n - 1, i -> i >= 1, i -> i - 1)
        .forEach(i -> System.out.println(" ".repeat(n - i) + "*".repeat(2 * i - 1)));
```

**Explanation:** Symmetry: top + bottom pyramid.

------------------------------------------------------------------------

## 🔥 2. Hollow Diamond

``` java
int n = 4;
IntStream.rangeClosed(1, n).forEach(i -> {
    String row = IntStream.rangeClosed(1, 2*n-1)
        .mapToObj(j -> (j == n-i+1 || j == n+i-1) ? "*" : " ")
        .collect(Collectors.joining());
    System.out.println(row);
});
```

**Explanation:** Print only boundary stars.

------------------------------------------------------------------------

## 🔥 3. Floyd's Triangle

``` java
AtomicInteger counter = new AtomicInteger(1);
IntStream.rangeClosed(1, 5).forEach(i -> {
    String row = IntStream.rangeClosed(1, i)
        .mapToObj(j -> String.valueOf(counter.getAndIncrement()))
        .collect(Collectors.joining(" "));
    System.out.println(row);
});
```

**Explanation:** Single running counter.

------------------------------------------------------------------------

## 🔥 4. Pascal's Triangle

``` java
int n = 5;
IntStream.range(0, n).forEach(i -> {
    AtomicInteger num = new AtomicInteger(1);
    String row = IntStream.rangeClosed(0, i)
        .mapToObj(j -> {
            int val = num.get();
            num.set(num.get() * (i - j) / (j + 1));
            return String.valueOf(val);
        }).collect(Collectors.joining(" "));
    System.out.println(" ".repeat(n - i) + row);
});
```

**Explanation:** Uses nCr formula.

------------------------------------------------------------------------

## 🔥 5. Zig-Zag Pattern

``` java
int rows=3, cols=9;
IntStream.range(0, rows).forEach(i -> {
    String row = IntStream.range(0, cols)
        .mapToObj(j -> ((i+j)%4==0 || (i==1 && j%4==2)) ? "*" : " ")
        .collect(Collectors.joining());
    System.out.println(row);
});
```

**Explanation:** Pattern repeats every 4 columns.

------------------------------------------------------------------------

## 🔥 6. Butterfly Pattern

``` java
int n=4;
IntStream.rangeClosed(1,n).forEach(i ->
    System.out.println("*".repeat(i)+" ".repeat(2*(n-i))+"*".repeat(i))
);
IntStream.iterate(n-1,i->i>=1,i->i-1).forEach(i ->
    System.out.println("*".repeat(i)+" ".repeat(2*(n-i))+"*".repeat(i))
);
```

**Explanation:** Mirror horizontally.

------------------------------------------------------------------------

## 🔥 7. Number Palindrome Pyramid

``` java
int n=4;
IntStream.rangeClosed(1,n).forEach(i->{
    String left = IntStream.iterate(i,x->x-1).limit(i)
        .mapToObj(String::valueOf).collect(Collectors.joining());
    String right = IntStream.rangeClosed(2,i)
        .mapToObj(String::valueOf).collect(Collectors.joining());
    System.out.println(" ".repeat(n-i)+left+right);
});
```

**Explanation:** Decrease then increase.

------------------------------------------------------------------------

## 🔥 8. X Pattern

``` java
int n=5;
IntStream.range(0,n).forEach(i->{
    String row = IntStream.range(0,n)
        .mapToObj(j -> (i==j || i+j==n-1)?"*":" ")
        .collect(Collectors.joining());
    System.out.println(row);
});
```

**Explanation:** Diagonals.

------------------------------------------------------------------------

## 🔥 9. Snake Pattern

``` java
int n=4;
AtomicInteger num=new AtomicInteger(1);
IntStream.range(0,n).forEach(i->{
    List<String> row = IntStream.range(0,n)
        .mapToObj(j -> String.valueOf(num.getAndIncrement()))
        .collect(Collectors.toList());
    if(i%2!=0) Collections.reverse(row);
    System.out.println(String.join(" ",row));
});
```

**Explanation:** Reverse alternate rows.

------------------------------------------------------------------------

## 🔥 10. Binary Triangle

``` java
int n=5;
IntStream.rangeClosed(1,n).forEach(i->{
    String row = IntStream.rangeClosed(1,i)
        .mapToObj(j -> String.valueOf((i+j)%2))
        .collect(Collectors.joining());
    System.out.println(row);
});
```

------------------------------------------------------------------------

## 🔥 11. Alphabet Pyramid

``` java
int n=4;
IntStream.rangeClosed(1,n).forEach(i->{
    String left = IntStream.range(0,i)
        .mapToObj(j -> String.valueOf((char)('A'+j)))
        .collect(Collectors.joining());
    String right = new StringBuilder(left.substring(0,left.length()-1)).reverse().toString();
    System.out.println(" ".repeat(n-i)+left+right);
});
```

------------------------------------------------------------------------

## 🔥 12. Hourglass Pattern

``` java
int n=4;
IntStream.iterate(n,i->i>=1,i->i-1)
    .forEach(i->System.out.println(" ".repeat(n-i)+"*".repeat(2*i-1)));
IntStream.rangeClosed(2,n)
    .forEach(i->System.out.println(" ".repeat(n-i)+"*".repeat(2*i-1)));
```

------------------------------------------------------------------------

## 🔥 13. Sandglass Pattern

(Similar to hourglass, reversed logic)

------------------------------------------------------------------------

## 🔥 14. Hollow Square with Diagonals

``` java
int n=5;
IntStream.range(0,n).forEach(i->{
    String row = IntStream.range(0,n)
        .mapToObj(j -> (i==0||i==n-1||j==0||j==n-1||i==j||i+j==n-1)?"*":" ")
        .collect(Collectors.joining());
    System.out.println(row);
});
```

------------------------------------------------------------------------

## 🔥 15. Spiral Matrix (Conceptual)

**Explanation:** Use boundaries (top, bottom, left, right). Streams are
not ideal here.

### Partial Stream Usage (Printing Only)
```java
Arrays.stream(matrix)
      .forEach(row -> {
          String line = Arrays.stream(row)
                  .mapToObj(val -> String.format("%4d", val))
                  .collect(Collectors.joining());
          System.out.println(line);
      });
```
```java
public class SpiralMatrix {

    public static void printSpiral(int n) {
        int[][] matrix = new int[n][n];

        int top = 0, bottom = n - 1;
        int left = 0, right = n - 1;
        int num = 1;

        while (top <= bottom && left <= right) {

            // Left → Right
            for (int j = left; j <= right; j++) {
                matrix[top][j] = num++;
            }
            top++;

            // Top → Bottom
            for (int i = top; i <= bottom; i++) {
                matrix[i][right] = num++;
            }
            right--;

            // Right → Left
            if (top <= bottom) {
                for (int j = right; j >= left; j--) {
                    matrix[bottom][j] = num++;
                }
                bottom--;
            }

            // Bottom → Top
            if (left <= right) {
                for (int i = bottom; i >= top; i--) {
                    matrix[i][left] = num++;
                }
                left++;
            }
        }

        // Print matrix
        for (int[] row : matrix) {
            for (int val : row) {
                System.out.printf("%4d", val);
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        printSpiral(4);
    }
}
```
------------------------------------------------------------------------

# 🧠 Interview Q&A

### Q1: When should you use streams for patterns?

**A:** When transformation is simple. Avoid for complex shapes.

### Q2: Why use AtomicInteger?

**A:** Streams require effectively final variables.

### Q3: map vs flatMap?

**A:** map → one-to-one, flatMap → flatten nested structures.

### Q4: Why are loops preferred sometimes?

**A:** Better readability and debugging.

------------------------------------------------------------------------

# 🎯 Final Tips

-   Always think in (row, col)
-   Identify symmetry
-   Convert visual → conditions
-   Practice edge cases

------------------------------------------------------------------------

# 🚀 End of Notes
