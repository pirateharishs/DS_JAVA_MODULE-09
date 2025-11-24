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
