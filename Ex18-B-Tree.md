# Ex18 Simulation of a Ticket Counter Using Queue (Linked List Implementation)
## AIM:
To simulate the functioning of a ticket counter that operates on a First-In-First-Out (FIFO) basis using a queue implemented via a linked list in Java.
## Algorithm
1. Start the program.
2. Create a Node class with variables to store customer data and a reference to the next node.
3. Create a Queue class with front and rear pointers and methods enqueue(), dequeue(), and display().
4. In enqueue(), add a new customer node at the rear end.
5. In dequeue(), remove the customer node from the front end and print the served customer.
6. Display the queue after each operation.
7. In the main() method, provide sample queue operations.
8. Stop the program.

## Program:
```
/*
Program to functioning of a ticket counter that operates on a First-In-First-Out (FIFO)
Developed by: kirthick roshan j
RegisterNumber: 212223040097
*/
class Node {
    String data;
    Node next;
    Node(String data) {
        this.data = data;
        this.next = null;
    }
}

class Queue {
    Node front, rear;
    
    void enqueue(String data) {
        Node newNode = new Node(data);
        if (rear == null) {
            front = rear = newNode;
            return;
        }
        rear.next = newNode;
        rear = newNode;
    }

    void dequeue() {
        if (front == null) {
            System.out.println("Queue is empty.");
            return;
        }
        System.out.println(front.data + " has been served.");
        front = front.next;
        if (front == null)
            rear = null;
    }

    void display() {
        if (front == null) {
            System.out.println("Queue is empty.");
            return;
        }
        Node temp = front;
        System.out.print("Current Queue: ");
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }
}

public class TicketCounter {
    public static void main(String[] args) {
        Queue q = new Queue();
        q.enqueue("Alice");
        q.enqueue("Bob");
        q.enqueue("Charlie");
        q.enqueue("Diana");
        q.display();
        q.dequeue();
        q.display();
    }
}
```

## Output:



<img width="1245" height="842" alt="image" src="https://github.com/user-attachments/assets/63852653-5138-4552-b9d7-ff8dff571edf" />

## Result:
Thus, the program successfully simulates a ticket counter queue where customers are served in FIFO order using a linked list-based queue implementation.
