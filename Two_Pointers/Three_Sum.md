# Solution Three Sum
## Approach
- Step 1: Core Concept: The main approach for this problem is the **Two Pointers** technique.
- Step 2: Sort: First, sort the array in ascending order.
- Step 3: Iterate: Loop through the numbers (note: only iterate up to `n - 2` since we need three elements).
- Step 4: Inside the loop:
    - Early exit: If the current number is strictly positive, stop. It is impossible to reach a sum of 0 with only positive numbers.
    - Skip duplicates: If the current number equals the previous one, skip it to prevent duplicate triplets.
    - Setup: Initialize a `target`, a left pointer `j` (right after the current number), and a right pointer `k` (at the end of the array).
    - Two Pointers logic:
        - If `nums[j] + nums[k] < target`, increment `j`.
        - If `nums[j] + nums[k] > target`, decrement `k`.
        - If they equal the `target`, save the result. Then, check for and skip any consecutive duplicate numbers on both pointers before moving them
        inward to continue checking.
  
## Complexity:
- Time: $O(N^2)$ — Sorting takes $O(N \log N)$ and the nested two-pointer traversal takes $O(N^2)$.
- Space: $O(1)$ or $O(N)$ — Depending on the space overhead of the language's built-in sorting algorithm.
## Solution
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector<vector<int>> result;
        int n = nums.size();
        for(int i = 0; i < n - 2; i++){
            if(nums[i] > 0) break;
            if(i > 0 && nums[i] == nums[i - 1]) continue;
            int target =  0 - nums[i];
            int j = i + 1, k = n - 1;
            while(j < k){
                if(nums[j] + nums[k] < target) j++;
                else if(nums[j] + nums[k] > target) k--;
                else {
                    result.push_back({nums[i], nums[j], nums[k]});
                    while (j < k && nums[j] == nums[j + 1]) j++;
                    while(j < k && nums[k] == nums[k - 1]) k--;
                    j++;
                    k--;
                }
            }
        }
        return result;
    }
};
```
## End
---
