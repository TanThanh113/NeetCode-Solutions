# Solution Longest Consecutive Sequence
## Approach
- Step 1: The core idea here is to use a hash set to store each unique number.
- Step 2: Initialize a variable to keep track of the longest sequence.
- Step 3: The core logic will be as follow
  - Iterate through the set.
  - Check if the `current number - 1` exists in the set. If it doesn't, this is the starting number of a sequence.
    If it does, continue to the next number.
  -  Check if the next consecutive number( `current number + 1`) exists. If it does, increment the length counter
     and keep searching until you reach the end of that sequence.
  -  Update the maximum length of the longest sequence.
## Complexity
- Time complexity: O(n) because each number is visited at most twice, the inner loop triggers at the start of a sequence.
- Space complexity: O(n) because required for the hash set to store the unique numbers.
```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_set<int> mySet(nums.begin(), nums.end());
        int longest = 0;
        for(int num : mySet){
            if(mySet.find(num - 1) == mySet.end()){
                int num_cur = num;
                int num_long = 1;
                while(mySet.find(num_cur + 1) != mySet.end()){
                    num_cur += 1;
                    num_long += 1;
                }
                longest = max(num_long, longest);
            }
        }
        return longest;
    }
};
```
## End
---
