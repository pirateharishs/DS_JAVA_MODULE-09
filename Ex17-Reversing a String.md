# Ex17 Reversing a String Using Stack Data Structure
## DATE: 01/10/25
## AIM:
To write a Java program that reverses an input string using a stack, without using built-in reverse functions.

## Algorithm
1. Start the program.
2. Create an empty stack of characters.
3. Traverse each character ch in the input string.
4. Create an empty StringBuilder named reversed.
5. While the stack is not empty.
6. Convert reversed to a string and return it.
7. Read the string input from the user.
8. Call and store the returned result in reversed.
9. Print the reversed string.
10. End the program.   

## Program:
```
/*
Program to reverses an input string using a stack
Developed by: HARISH S
Register Number: 212223230071
*/

import java.util.Scanner;
import java.util.Stack;

public class ReverseStringWithStack {

    public static String reverseString(String input) {
        Stack<Character> stack = new Stack<>();
        for (char ch : input.toCharArray()) {
            stack.push(ch);
        }
        StringBuilder reversed = new StringBuilder();
        while (!stack.isEmpty()) {
            reversed.append(stack.pop());
        }

        return reversed.toString();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine();
        String reversed = reverseString(input);

        // Display result
        System.out.println(reversed);

        scanner.close();
    }
}

```

## Output:

<img width="467" height="339" alt="image" src="https://github.com/user-attachments/assets/72f8e832-0d20-4766-b7c1-580040bb803e" />


## Result:
Thus, the program successfully reverses the given string using a stack without relying on built-in reverse functions.
