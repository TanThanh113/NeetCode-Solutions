# Solution Products of Array Except Self
## Approach
- Step 1: The core idea is that the product of an element except itself equals the product of all elements to
its left multiplied by the product of all elements to its right.

- Step 2: Use a single result array to store and calculate these products.

- Step 3: Iterate through the array: first from left to right to calculate the left products, then from right to 
left to multiply by the right products.

## Complexity:
- Time complexity: O(n) because we traverse the array twice.
- Space complexity: O(1)(excluding the output array) since we compute the values directly into the result array
  without using extra data structures.
```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int> res(nums.size(), 1);
        int left = 1;
        for(int i = 0; i < nums.size(); i++){
            res[i] = left;
            left *= nums[i];
        }
        int right = 1;
        for(int i = nums.size() - 1; i >= 0; i--){
            res[i] *= right;
            right *= nums[i];
        }
        return res;
    }
};
```
## End
---
