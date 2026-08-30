# Solution Valid Parentheses
## Approach
- Step 1: The core idea of this problem is to use a `stack` to store the brackets.
- Step 2: Inside the loop, we only need to do two things:
  - If it's an opening bracket, `push` it onto the stack.
  - If it's a closing bracket, check the `top` element of the stack. If it matches the corresponding opening bracket,
    `pop` it from the stack. If it doesn't match (or the stack is empty), `return false`.
## Complexity
- Time complexity: `O(N)` - We iterate through the string exactly once (`N` is the string length).
- Space complexity: `O(N)` - In the worst case (e.g., all opening brackets), the stack will store all `N` characters.
```cpp
class Solution {
public:
    bool isValid(string s) {
        vector<char> stack; 
        for(int i = 0; i < s.length(); i++){
            if(s[i] == '(' || s[i] == '[' || s[i] == '{'){
                stack.push_back(s[i]);
            } else {
                if(stack.empty()) return false;
                char top = stack.back();
                if( (s[i] == ')' && top == '(') ||
                    (s[i] == ']' && top == '[') ||
                    (s[i] == '}' && top == '{') ){
                        stack.pop_back();
                } else {
                    return false;
                }
            }
        }
        return stack.empty();
    }
};
```
## End
---
