# Solution Min Stack
## Approach
- Step 1: Since the problem requires an OOP approach, first create a `private` section and declare 3 variables: `top_idx`, `arr`, and `min_arr`.
- Step 2: Write the `MinStack()` constructor and initialize `top_idx = -1` inside it.
- Step 3: Write the `push` function, which does the following in order:
  - Increment the top index by 1.
  - Assign the value to the array (`arr[top_idx] = val`).
  - Check the minimum condition to store the correct value into the `min_arr` array.
- Step 4: Write the `pop` function, simply decrementing the top index (`top--` or `top_idx--`).
- Step 5: Write the `top` and `getMin` functions, which are quite similar, by returning the value at the `top_idx` position from their respective arrays.
## Complexity
- Time Complexity: $O(1)$ for all operations (`push`, `pop`, `top`, `getMin`).
- Space Complexity: $O(N)$, where $N$ is the maximum number of elements in the stack.
## Solution
```cpp
class MinStack {
private:
    int top_idx;
    int arr[30005];
    int min_arr[30005];
public:
    MinStack() {
        top_idx = -1;
    }
    
    void push(int val) {
        top_idx++;
        arr[top_idx] = val;
        if(top_idx == 0){
            min_arr[top_idx] = val;
        } else {
            min_arr[top_idx] = min(val, min_arr[top_idx - 1]);
        }
    }
    
    void pop() {
        if(top_idx >= 0){
            top_idx--;
        }
    }
    
    int top() {
        return arr[top_idx];
    }
    
    int getMin() {
        return min_arr[top_idx];
    }
};
```
## End
---
