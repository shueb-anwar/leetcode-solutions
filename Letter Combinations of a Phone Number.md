#  Letter Combinations of a Phone Number

Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent. Return the answer in `any order`.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.
 

**Example 1:**

![alt text](200px-Telephone-keypad2.svg.png "Logo Title Text 1")

```
Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

**Example 2:**
```
Input: digits = ""
Output: []
```
**Example 3:**
```
Input: digits = "2"
Output: ["a","b","c"]
``` 

**Constraints:**

- `0 <= digits.length <= 4`
- `digits[i]` is a digit in the range `['2', '9']`


```
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function(digits) {
    this.numberMap = {"2":"abc", "3":"def", "4": "ghi", "5":"jkl","6":"mno", "7":"pqrs", "8":"tuv","9":"wxyz"}
    if(!digits.length || digits == '1') return [];
    
    if(digits.length == 1) return numberMap[digits].split('');
    
    let combos = new Combinations(digits, numberMap);
    combos.getCombinations(0, "");
    
    return combos.answers;
    
};

function Combinations(digits, numberMap) {
    this.answers = [];
    this.digits = digits;
    this.numberMap = numberMap;
}

Combinations.prototype.getCombinations = function(index, str) {
    if (str.length === this.digits.length) {
        this.answers.push(str);
        return;
    }

    let letter_lists = this.numberMap[this.digits[index]];

    for(let i = 0; i < letter_lists.length; i++) {
        let newString = str + letter_lists[i];
        this.getCombinations(index + 1, newString);
    }
}
```