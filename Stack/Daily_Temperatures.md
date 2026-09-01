# Solution Daily Temperatures
## Approach
- Step 1: The main idea is to use a stack to store the **indices** of the days, not the temperatures themselves.
- Step 2: Initialize a `results` array with 0s and an empty `stack`.
- Step 3: Iterate through the `temperatures` array using an index `i`:
  - While the stack is not empty and the current temperature is greater than the temperature at the index on the top of the stack, it means we found a warmer day.
  - Pop the top index from the stack, calculate the waiting days (`i - prev`), and save it in the `results` array.
  - Push the current index `i` onto the stack.
- Step 4: Return the `results` array.
## Complexity
- Time Complexity: $O(N)$, where $N$ is the number of days. Each element is pushed and popped from the stack exactly once.
- Space Complexity: $O(N)$ for storing the stack and the results array.
## Solution
```cpp
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& temperatures) {
        vector<int> stack;
        vector<int> results(temperatures.size(), 0);
        for(int i = 0; i < temperatures.size(); i++){
            while(!stack.empty() && temperatures[i] > temperatures[stack.back()]){
                int prev = stack.back();
                stack.pop_back();
                results[prev] = i - prev;
            }
            stack.push_back(i);
        }
        return results;
    }
};
```
## End
---
