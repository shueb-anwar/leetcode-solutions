#  Longest Valid Parentheses

Given a string containing just the characters `'('` and `')'`, find the length of the longest valid (well-formed) parentheses substring.

 

**Example 1:**
```
Input: s = "(()"
Output: 2
Explanation: The longest valid parentheses substring is "()".
```

**Example 2:**
```
Input: s = ")()())"
Output: 4
Explanation: The longest valid parentheses substring is "()()".
```

**Example 3:**
```
Input: s = ""
Output: 0
``` 

**Constraints:**

- `0 <= s.length <= 3 * 104`
- `s[i]` is `'('`, or `')'`.


```
/**
 * @param {string} s
 * @return {number}
 * Time complexity : O ( n² ) and Space complexity : O ( 1 )
 */
var longestValidParentheses = function(s) {
    var count = 0;
    var max = 0;
    
    for (var i = 0; i < s.length; i++) {
        count = 0;
        
        for (var j = i; j < s.length; j++) {
            if (s.charAt(j) == '(') {
                count++;
            } else {
                count--;
            }
            if (count < 0) {
                break;

            }
            if (count == 0) {
                if (j - i + 1 > max) {
                    max = j - i + 1;
                }
            }
        }
    }
    
    return max;
};
```