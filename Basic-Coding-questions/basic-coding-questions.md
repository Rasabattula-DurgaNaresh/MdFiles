# 1. Reverse a String 

```java
 public static void revrse(String[] args) { 
        String str = "hello"; 
        String rev = ""; 
         
        for (int i = str.length() - 1; i >= 0; i--) { 
            rev += str.charAt(i); 
        } 
         
        System.out.println(rev); 
    }
```

# 2. Check Palindrome

```java
 public static void checkPalindrome(String[] args) { 
        String str = "madam"; 
        String rev = new StringBuilder(str).reverse().toString(); 
         
        if (str.equals(rev)) 
            System.out.println("Palindrome"); 
        else 
            System.out.println("Not Palindrome"); 
    } 
```

