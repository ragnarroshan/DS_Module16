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
