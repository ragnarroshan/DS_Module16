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
