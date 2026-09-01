# Solution Evaluate Reverse Polish Notation
## Approach
- Step 1: The main idea of this problem is to use a stack to store numbers.
- Step 2: Iterate through each element in the array:
  - If it is a number, push it onto the stack.
  - If it is an operator, pop the numbers from the stack to perform the calculation.
## Complexity
- Time Complexity: $O(N)$, where $N$ is the total number of elements in the `tokens` array (since we iterate through the array exactly once).
- Space Complexity: $O(N)$, because in the worst-case scenario, the stack will store all the numbers before any operations are performed.
## Solution
```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens){
        vector<int> stack;
        
        for(string token : tokens) {
            if(token == "+" || token == "-" || token == "*" || token == "/") {
                int right = stack.back(); stack.pop_back();
                int left = stack.back(); stack.pop_back();
                
                if(token == "+") stack.push_back(left + right); 
                else if(token == "-") stack.push_back(left - right);
                else if(token == "*") stack.push_back(left * right);
                else if(token == "/") stack.push_back(left / right);
            } 
            else {
                stack.push_back(stoi(token));
            }
        }
        return stack.back();
    }
};
```
## End
---
