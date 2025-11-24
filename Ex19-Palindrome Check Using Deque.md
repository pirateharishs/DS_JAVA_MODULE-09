# Ex19 Palindrome Check Using Deque
## DATE: 08/10/25
## AIM:
To design a program that checks whether a given message is a palindrome by removing all non-alphanumeric characters, converting all characters to lowercase, and using a deque data structure for comparison.

## Algorithm
1. Start the program.
2. Read the input string message.
3. Convert the string to lowercase.
4. Remove all non-alphanumeric characters using a regular expression.
5. Create an empty Deque (double-ended queue).
6. For each character c in the cleaned string.
7. While the deque contains more than one character.
8. If all pairs matched (or string has 0/1 character), return true.
9. If return value is true → print "Palindrome" , Otherwise → print "Not a palindrome".
10. End the program.   

## Program:
```
/*
Program to checks whether a given message is a palindrome by removing all non-alphanumeric characters.
Developed by: HARISH S
Register Number: 212223230071
*/

import java.util.*;

public class PalindromeChecker {
    
    public static boolean isPalindrome(String message) {
        // Convert to lowercase and remove non-alphanumeric characters
        message = message.toLowerCase().replaceAll("[^a-z0-9]", "");
        
        Deque<Character> deque = new ArrayDeque<>();
        
        // Add all characters to the deque
        for (char c : message.toCharArray()) {
            deque.addLast(c);
        }
        
        // Compare characters from both ends
        while (deque.size() > 1) {
            if (deque.pollFirst() != deque.pollLast()) {
                return false;  // Mismatch found
            }
        }
        
        return true;  // All characters matched
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        //System.out.println("Enter a message:");
        String input = scanner.nextLine();

        if (isPalindrome(input)) {
            System.out.println("Palindrome");
        } else {
            System.out.println("Not a palindrome");
        }

        scanner.close();
    }
}

```

## Output:

<img width="459" height="252" alt="image" src="https://github.com/user-attachments/assets/e038d3e3-303b-4f2c-8b5a-87ee42c3172c" />

## Result:
The program successfully removes all non-alphanumeric characters, converts the text to lowercase, and uses a deque to efficiently compare characters from both ends. Hence, it determines whether the string is a palindrome.
