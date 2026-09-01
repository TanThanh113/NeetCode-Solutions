# Solution Car Fleet
## Approach
- Step 1: The main idea is to combine each car's starting position and the time it takes to reach the target into a pair, then process them from closest to furthest.
- Step 2: Iterate through the arrays to calculate the time `(target - position) / speed` for each car and store it in a vector of pairs: `{position, time}`.
- Step 3: Sort the array of pairs in descending order (`rbegin()` to `rend()`) so that the cars closest to the target are evaluated first.
- Step 4: Create a `stack` to keep track of the fleets. Iterate through the sorted cars:

  - If the stack is empty, or the current car's time is strictly greater than the time at the top of the stack (meaning it is too slow to catch up to the fleet ahead), push its time onto the stack to form a new fleet.
  - Otherwise, it catches up and joins the fleet ahead, so we do nothing.
- Step 5: Return `stack.size()`, which represents the total number of car fleets.
## Complexity
- Time Complexity: $O(N \log N)$ where $N$ is the number of cars, mainly due to the sorting step. The for-loops take $O(N)$ time.
- Space Complexity: $O(N)$ to store the array of pairs (`cars`) and the `stack`.
## Solution
```cpp
class Solution {
public:
    int carFleet(int target, vector<int>& position, vector<int>& speed) {
        vector<pair<int, double>> cars(position.size());
        for(int i = 0; i < position.size(); i++){
            double time = (double)(target - position[i]) / speed[i]; 
            cars[i] = {position[i], time};
        }
        sort(cars.rbegin(), cars.rend());
        vector<double> stack;
        for(int i = 0; i < position.size(); i++){
            double time = cars[i].second;
            if(stack.empty() || time > stack.back()){
                stack.push_back(time);
            }
        }
        return stack.size();
    }
};
```
## End
---
