# Leetcode_Day79
# Day 79: Valid Parentheses

**LeetCode Problem:** 20. Valid Parentheses  
**Difficulty:** Easy  
**Language:** Java  
**Topic:** Stack, String

## Problem Statement

Given a string `s` containing only the characters `(`, `)`, `{`, `}`, `[` and `]`, determine whether the input string is valid.

A string is valid if:
1. Every opening bracket has a matching closing bracket of the same type.
2. Brackets are closed in the correct order.
3. Every closing bracket has a corresponding opening bracket.

## Approach: Stack

I used a Stack to check whether the brackets are properly balanced.

1. Create a stack to store opening brackets.
2. Traverse the string character by character.
3. If the character is an opening bracket (`(`, `{`, `[`), push it onto the stack.
4. If it is a closing bracket:
   - Return `false` if the stack is empty.
   - Pop the top element and check whether it matches the closing bracket.
   - Return `false` if the brackets do not match.
5. After processing the entire string, return `true` only if the stack is empty.

The stack follows the **Last In, First Out (LIFO)** principle, which makes it suitable for checking nested brackets.

## Java Solution

```java
import java.util.Stack;

class Solution {
    public boolean isValid(String s) {
        Stack<Character> st = new Stack<>();

        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);

            if (ch == '(' || ch == '{' || ch == '[') {
                st.push(ch);
            } else {
                if (st.isEmpty()) {
                    return false;
                }

                char top = st.pop();

                if ((ch == ')' && top != '(')
                    || (ch == '}' && top != '{')
                    || (ch == ']' && top != '[')) {
                    return false;
                }
            }
        }

        return st.isEmpty();
    }
}

```
Example
Input:
s = "()[]{}"

Output:
true

Explanation:

Every opening bracket has a matching closing bracket, and all brackets close in the correct order.
Complexity Analysis
- Time Complexity: O(n), where n is the length of the string, because each character is processed once.
- Space Complexity: O(n) in the worst case, when all characters are opening brackets and must be stored in the stack.
What I Learned
- How to use a stack to solve bracket-matching problems.
- Why the LIFO principle is useful for nested structures.
- How to handle mismatched brackets and closing brackets without a corresponding opening bracket.
- Why checking whether the stack is empty at the end is important.
Takeaway
Sometimes, the best way to solve a problem is to choose a data structure that naturally fits the problem. A stack makes tracking nested brackets simple and efficient.

Day 79 complete! One more problem solved, one more concept understood.
