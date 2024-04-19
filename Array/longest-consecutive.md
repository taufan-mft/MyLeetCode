Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.

 

Example 1:

Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.

Example 2:

Input: nums = [0,3,7,2,5,8,4,6,0,1]

Output: 9

---
Solution:
```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_set<int>s(nums.begin(), nums.end());
        int longest = 0;
        for(auto &n: s){
            //if this is the start of the sequence
            if(!s.count(n - 1)){
                int length = 1; 
                while(s.count(n + length))
                    ++length;
                longest = max(longest, length);
            } 

        }
        return longest;
    }
};
```
Explanation:

- We create a set that store all the numbers from vector `nums`. This is crucial so we can fastly check if a number exists by using `s.count()`. Another reason is we don't want any duplicates so it doesn't distort the length calculation.
- We store the longest length in variable `longest` start at 0.
- Loop thru each number in the set `s`, check if the number before that exists by using `s.count(n-1)`.
- If that doesn't exists, then we encounter the start of the path. Start counting the length.
- We will keep adding the length until `n+1` doesn't exists--the sequence ends there.
- Update the longest using `max()`. max will only keep the biggest number