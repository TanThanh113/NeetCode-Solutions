# Solution Valid Palindrome
## Approach
- Step 1: The main idea of this problem is to use the `two pointers` technique to traverse the string from both ends.
- Step 2: Run a loop with the condition `left < right`.
- Step 3: Inside the loop:
  - Check if `s[left]` and `s[right]` are alphanumeric characters. If not, skip them and move to the next character.
  - Finally, check if `s[left] == s[right]`. If they do not match, exit the loop and return `false`.
## Complexity
- Time Complexity: $O(N)$, where $N$ is the length of the string. Each character in the string is traversed at most once.
- Space Complexity: $O(1)$. We only use two variables, `left` and `right`, to keep track of the positions, without allocating any new strings 
or arrays, ensuring minimal memory usage.
## Solution
```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        int left = 0;
        int right = s.size() - 1;
        while (left < right){
            while (left < right && !isalnum(s[left])){
                left++;
            }
            while (left < right && !isalnum(s[right])){
                right--;
            }
            if (tolower(s[left]) != tolower(s[right])) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
};
```
## End
---
