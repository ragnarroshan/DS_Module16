# Ex16 Check for Balanced Parentheses Using Stack
## AIM:
To write a Java program that verifies whether the parentheses (brackets) in an input string are balanced — meaning each opening bracket (, {, [ has a corresponding and correctly ordered closing bracket ), }, ].

## Algorithm
1. Start the program.
2. Create a stack to store opening brackets.
3. Traverse each character in the input string.
4. If the character is an opening bracket, push it onto the stack.
5. If it is a closing bracket, check if the stack is empty or if it does not match the top element; if so, return unbalanced.
6. If it matches, pop the top element from the stack.
7. After processing all characters, if the stack is empty then the parentheses are balanced, otherwise they are not.
8. Stop the program. 

## Program:
```
/*
Program to verify whether the parentheses (brackets) in an input string are balanced
Developed by: kirthick roshan j
RegisterNumber: 212223040097
*/
import java.util.*;

public class BalancedParentheses {
    public static boolean isBalanced(String str) {
        Stack<Character> stack = new Stack<>();

        for (char c : str.toCharArray()) {
            // Push opening brackets
            if (c == '(' || c == '{' || c == '[') {
                stack.push(c);
            }
            // Check closing brackets
            else if (c == ')' || c == '}' || c == ']') {
                if (stack.isEmpty()) {
                    return false;
                }
                char top = stack.pop();

                // Check for matching pairs
                if ((c == ')' && top != '(') ||
                    (c == '}' && top != '{') ||
                    (c == ']' && top != '[')) {
                    return false;
                }
            }
        }

        // If stack empty, it's balanced
        return stack.isEmpty();
    }

    public static void main(String[] args) {
        String input = "({[]})";

        if (isBalanced(input)) {
            System.out.println("Balanced Parentheses");
        } else {
            System.out.println("Not Balanced");
        }
    }
}
```

## Output:
<img width="443" height="361" alt="image" src="https://github.com/user-attachments/assets/37bcf4b3-651c-43a2-957a-1eefd1c4bb02" />



## Result:
Thus,the program correctly checks whether an input string has balanced parentheses using a stack.




# Ex17 Reversing a String Using Stack Data Structure
## AIM:
To write a Java program that reverses an input string using a stack, without using built-in reverse functions.

## Algorithm
1. Start the program.
2. Create an empty stack to store characters.
3. Read the input string from the user.
4. Push each character of the string onto the stack.
5. Pop characters from the stack one by one and append them to a new string (reversed string).
6. Print the reversed string.
7. Stop the program   
 

## Program:
```
/*
Program to reverses an input string using a stack
Developed by: kirthick roshan j
RegisterNumber: 212223040097
*/
import java.util.Stack;
import java.util.Scanner;

public class ReverseStringStack {
    public static void main(String[] args) {
        Stack<Character> stack = new Stack<>();
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String input = sc.nextLine();

        for (char ch : input.toCharArray()) {
            stack.push(ch);
        }

        String reversed = "";
        while (!stack.isEmpty()) {
            reversed += stack.pop();
        }

        System.out.println("Reversed String: " + reversed);
    }
}

```

## Output:

<img width="467" height="339" alt="image" src="https://github.com/user-attachments/assets/72544616-7bcf-4f0a-8680-405d34772b84" />


## Result:
Thus, the program successfully reverses the given string using a stack without relying on built-in reverse functions.

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


# Ex19 Palindrome Check Using Deque
## AIM:
To design a program that checks whether a given message is a palindrome by removing all non-alphanumeric characters, converting all characters to lowercase, and using a deque data structure for comparison.

## Algorithm
1. Start the program and read the input message from the user.
2. Create an empty deque to store characters.
  
3. Traverse each character of the input string:

   If the character is alphanumeric, convert it to lowercase and insert it at the rear of the deque.
  
4. While the deque contains more than one character:

   Remove and compare characters from the front and rear.

   If the characters are not equal, return false.

5. If all comparisons match, return true and print that the string is a palindrome.

6. Stop the program.

## Program:
```
/*
Program to checks whether a given message is a palindrome by removing all non-alphanumeric characters.
Developed by: kirthick roshan j
RegisterNumber: 212223040097
*/
import java.util.*;

public class PalindromeDeque {
    public static boolean isPalindrome(String str) {
        Deque<Character> deque = new LinkedList<>();
        for (char c : str.toCharArray()) {
            if (Character.isLetterOrDigit(c)) {
                deque.add(Character.toLowerCase(c));
            }
        }

        while (deque.size() > 1) {
            if (deque.removeFirst() != deque.removeLast())
                return false;
        }
        return true;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a message: ");
        String message = sc.nextLine();
        if (isPalindrome(message))
            System.out.println("Palindrome");
        else
            System.out.println("Not a Palindrome");
        sc.close();
    }
}
```

## Output:


<img width="459" height="252" alt="image" src="https://github.com/user-attachments/assets/51be7ab8-3e5b-44d1-a74d-6a63a9c2ed34" />


## Result:
The program successfully removes all non-alphanumeric characters, converts the text to lowercase, and uses a deque to efficiently compare characters from both ends. Hence, it determines whether the string is a palindrome.


# Ex20 Sorting an Array using Merge Sort Algorithm
## AIM:
To design a program that sorts a given array of integers in ascending order without using built-in sorting functions, achieving O(n log n) time complexity and minimal space usage.
## Algorithm
1. Start the program.
2. Read the size of the array and input its elements.
3. Use the merge sort function:
   
   Divide the array into two halves recursively until each sub-array has one element.

4. Merge the sorted halves:
 
   Compare the elements of both halves

5. Insert the smallest element into the new array and continue until both halves are merged.

6. Print the sorted array.

7. Stop the program.  

## Program:
```
/*
Program tosorts a given array of integers in ascending order without using built-in sorting functions
Developed by: kirthick roshan j
RegisterNumber: 212223040097
*/
import java.util.*;

public class MergeSort {
    
    // Merge function
    public static void merge(int arr[], int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        int L[] = new int[n1];
        int R[] = new int[n2];

        for (int i = 0; i < n1; ++i)
            L[i] = arr[left + i];

        for (int j = 0; j < n2; ++j)
            R[j] = arr[mid + 1 + j];

        int i = 0, j = 0;
        int k = left;

        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            } else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }

        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }

        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }

    // Merge Sort function
    public static void mergeSort(int arr[], int left, int right) {
        if (left < right) {
            int mid = (left + right) / 2;

            mergeSort(arr, left, mid);
            mergeSort(arr, mid + 1, right);
            merge(arr, left, mid, right);
        }
    }

    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();

        int arr[] = new int[n];
        System.out.println("Enter elements:");
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        mergeSort(arr, 0, n - 1);

        System.out.println("Sorted Array:");
        for (int x : arr)
            System.out.print(x + " ");
        System.out.println();

        sc.close();
    }
}
```

## Output:


<img width="620" height="297" alt="image" src="https://github.com/user-attachments/assets/a59de798-48be-4bb0-976f-fcb5bac1a2a8" />


## Result:
The program has been successfully implemented and executed.
It sorts the given array of integers in ascending order using the Merge Sort algorithm with a time complexity of O(n log n) and minimal extra space.


