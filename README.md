# Ex16 Check for Balanced Parentheses Using Stack
## DATE: 26/09/25
## AIM:
To write a Java program that verifies whether the parentheses (brackets) in an input string are balanced — meaning each opening bracket (, {, [ has a corresponding and correctly ordered closing bracket ), }, ].

## Algorithm
1. Start the program.
2. Stack Initialization.
3. Read the input string.
4. Create a stack st of size expr.length().
5. Repeat for each character in the string.
6. Opening Parentheses.
7.  Closing Parentheses.
8.  After Processing All Characters, if the stack is empty return true.
9.  If stack is not empty return false.
10.  Print the result.
11.  End the program.   

## Program:
```
/*
Program to verify whether the parentheses (brackets) in an input string are balanced
Developed by: HARISH S
Register Number: 212223230071
*/

import java.util.Scanner;

class ArrayStack {
    private char[] stack;
    private int top;

    public ArrayStack(int size) {
        stack = new char[size];
        top = -1;
    }

    public void push(char ch) {
        stack[++top] = ch;
    }

    public char pop() {
        return stack[top--];
    }

    public boolean isEmpty() {
        return top == -1;
    }
}

public class ParenChecker {
    public static boolean isBalanced(String expr) {
        ArrayStack st = new ArrayStack(expr.length());
        for (char ch : expr.toCharArray()) {
            if (ch == '(' || ch == '{' || ch == '[') {
                st.push(ch);
            } else if (ch == ')' || ch == '}' || ch == ']') {
                if (st.isEmpty()) return false;
                char top = st.pop();
                if ((ch == ')' && top != '(') ||
                    (ch == '}' && top != '{') ||
                    (ch == ']' && top != '[')) {
                    return false;
                }
            }
        }
        return st.isEmpty();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String expr = sc.nextLine();
        boolean ok = isBalanced(expr);
        System.out.println(ok);
        sc.close();
    }
}

```

## Output:

<img width="443" height="361" alt="image" src="https://github.com/user-attachments/assets/d8a974a9-2caa-46b2-8f1c-5854a59bf1b2" />

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

# Ex18 Simulation of a Ticket Counter Using Queue (Linked List Implementation)
## DATE: 03/10/25
## AIM:
To simulate the functioning of a ticket counter that operates on a First-In-First-Out (FIFO) basis using a queue implemented via a linked list in Java.
## Algorithm
1. Start program.
2. Queue Initialization.
3. Queue Operations.
4. DISPLAY Operation.
5. Main Simulation.
6. End the program.   

## Program:
```
/*
Program to functioning of a ticket counter that operates on a First-In-First-Out (FIFO)
Developed by: HARISH S
Register Number: 212223230071
*/

import java.util.Scanner;
class Node {
    String customerName;
    Node next;

    public Node(String name) {
        this.customerName = name;
        this.next = null;
    }
}

class TicketQueue {
    private Node front;
    private Node rear;

    public TicketQueue() {
        this.front = this.rear = null;
    }

    public void enqueue(String customerName) {
        Node newNode = new Node(customerName);
        if (rear == null) {
            front = rear = newNode;
        } else {
            rear.next = newNode;
            rear = newNode;
        }
    }

    public void dequeue() {
        if (front == null) {
            System.out.println("Queue is empty. No customer to serve.");
            return;
        }
        System.out.println("Serving customer: " + front.customerName);
        front = front.next;
        if (front == null) rear = null;
    }

    public void displayQueue() {
        if (front == null) {
            System.out.println("Queue is empty.");
            return;
        }
        Node temp = front;
        System.out.print("Queue: ");
        while (temp != null) {
            System.out.print(temp.customerName);
            if (temp.next != null) System.out.print(" -> ");
            temp = temp.next;
        }
        System.out.println();
    }
}

public class TicketCounter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        TicketQueue queue = new TicketQueue();

        while (true) {
            if (!scanner.hasNextLine()) break;
            String command = scanner.nextLine().trim();
            if (command.isEmpty()) continue;

            String[] parts = command.split(" ");

            switch (parts[0]) {
                case "enqueue":
                    if (parts.length >= 2) queue.enqueue(parts[1]);
                    break;
                case "dequeue":
                    queue.dequeue();
                    break;
                case "display":
                    queue.displayQueue();
                    break;
                case "exit":
                    System.out.println("Exiting simulation.");
                    scanner.close();
                    return;
            }
        }
        scanner.close();
    }
}

```

## Output:

<img width="1245" height="842" alt="image" src="https://github.com/user-attachments/assets/1e3f40a6-7f61-4ba7-85b7-34445df03ea7" />

## Result:
Thus, the program successfully simulates a ticket counter queue where customers are served in FIFO order using a linked list-based queue implementation.

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

# Ex20 Sorting an Array using Merge Sort Algorithm
## DATE: 10/10/25
## AIM:
To design a program that sorts a given array of integers in ascending order without using built-in sorting functions, achieving O(n log n) time complexity and minimal space usage.
## Algorithm
1. Start the program.
2. Read integer n.
3. Create an array nums of size n.
4. Read n integers from the user and store them into nums.
5. Call the function sortArray(nums).
6. Call heapSort(nums).
7. Return the sorted array.
8. Build Max Heap.
9. Extract Elements One by One.
10. End the program.  

## Program:
```
/*
Program tosorts a given array of integers in ascending order without using built-in sorting functions
Developed by: HARISH S
Register Number: 212223230071
*/

import java.util.*;
public class Solution {
    
    private void swap(int[] arr, int index1, int index2) {
        int temp = arr[index1];
        arr[index1] = arr[index2];
        arr[index2] = temp;
    }

    // Heapify the subtree rooted at index i
    private void heapify(int[] arr, int n, int i) {
        int largest = i; 
        int left = 2 * i + 1;
        int right = 2 * i + 2; 

        if (left < n && arr[left] > arr[largest]) {
            largest = left;
        }

        if (right < n && arr[right] > arr[largest]) {
            largest = right;
        }

        if (largest != i) {
            swap(arr, i, largest); 
            heapify(arr, n, largest);
        }
    }

    private void heapSort(int[] arr) {
        int n = arr.length;
        for (int i = n / 2 - 1; i >= 0; i--) {
            heapify(arr, n, i);
        }

        for (int i = n - 1; i >= 0; i--) {
            swap(arr, 0, i);
            heapify(arr, i, 0);
        }
    }

    public int[] sortArray(int[] nums) {
        heapSort(nums);
        return nums;
    }

    // ------------------ MAIN METHOD ------------------
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution solution = new Solution();

        //System.out.println("Enter number of elements:");
        int n = sc.nextInt();
        
        int[] nums = new int[n];
        //System.out.println("Enter " + n + " elements:");
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        int[] sorted = solution.sortArray(nums);
        System.out.println("Sorted array:");
        System.out.println(Arrays.toString(sorted));

        sc.close();
    }
}

```

## Output:

<img width="620" height="297" alt="image" src="https://github.com/user-attachments/assets/5fc90908-90ae-4e4d-9ab6-e2c41a45e87a" />

## Result:
The program has been successfully implemented and executed.
It sorts the given array of integers in ascending order using the Merge Sort algorithm with a time complexity of O(n log n) and minimal extra space.



## Result:
Thus,the program correctly checks whether an input string has balanced parentheses using a stack.
