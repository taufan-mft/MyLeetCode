Problem:https://leetcode.com/problems/valid-palindrome/description/

---
Solution:
```cpp
class Solution {
public:
    bool isPalindrome(string s) {

        if (s.empty()) {
            return true;
        }
        int left = 0;
        int right = s.size() - 1;
        while (left < right) {
            while(left < right && !isalnum(s[left])) {
                left++;
            }
            while(left < right && !isalnum(s[right])) {
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
Explanation:

- Skip checking if it's an empty string.
- Initialize two pointers. One is on the beginning, and the other is on the end of the array.
- While the left pointer is smaller then right pointer (meaning the two haven't met), do two loops to check if either the two pointer met with non alnum character. If it does, then increment the pointer.
- This effectively ignores non alnum characters.
- Then check if the character is the same, if not the same, then it's not palindrome.