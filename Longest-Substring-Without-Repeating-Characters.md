# Longest Substring Without Repeating Characters

Given a string `s`, find the length of the longest substring without repeating characters.

 

Example 1:
```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

Example 2:
```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

Example 3:
```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
``` 

Constraints:

- `0 <= s.length <= 5 * 10<sup>4</sup>`
- `s` consists of English letters, digits, symbols and spaces.

```
/**
 * @param {string} s
 * @return {number}
 */

var lengthOfLongestSubstring = function (s) {
    // Initialise an array to store the running characters and a longest string length variable
    let currentString = [];
    let longestStringLength = 0;

    // Loop through the provided string
    for (let i = 0; i < s.length; i++) {
        // Attempt to get the current character's position in the current string
        const currentCharacterPosition = currentString.indexOf(s[i]);

        // Check if the current character exists in the current string
        if (currentCharacterPosition !== -1) {
            // Chop the array off after the occurence of the character
            currentString.splice(0, currentCharacterPosition + 1);
        }

        // Add the current character to the array
        currentString.push(s[i]);

        // Store the current string length if bigger than the existing record
        longestStringLength = Math.max(
            longestStringLength,
            currentString.length
        );
    }

    return longestStringLength;
};
```