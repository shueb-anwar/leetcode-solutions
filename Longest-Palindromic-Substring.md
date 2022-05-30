#  Longest Palindromic Substring

Given a string s, return the longest palindromic substring in s.

 

**Example 1:**
```
Input: s = "babad"
Output: "bab"
Explanation: "aba" is also a valid answer.
```

**Example 2:**
```
Input: s = "cbbd"
Output: "bb"
```

**Constraints:**

- `1 <= s.length <= 1000`
- `s` consist of only digits and English letters.

```
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function (s) {
    var current = 0, len = s.length, maxl = 0, maxr = 0, end = len;
    
    for (var current = 0; current < end; current++) {
        calculate(current, current);
        calculate(current, current + 1);
    } 
    
    function calculate(left, right) {
        while (left > -1 && right < len && s[left] === s[right]) {
            if (maxr - maxl < right - left) {
                maxl = left;
                maxr = right;
                end = len - (maxr - current);
            }
            
            left--;
            right++;
        }
    }

    return s.slice(maxl, maxr + 1);
};
```