#  Add Binary

Given two binary strings `a` and `b`, return their sum as a binary string.

**Example 1**:
```
Input: a = "11", b = "1"
Output: "100"
```
**Example 2**:
```
Input: a = "1010", b = "1011"
Output: "10101"
```

**Constraints**:

- `1 <= a.length, b.length <= 104`
- `a` and `b` consist only of `'0'` or `'1'` characters.
- Each string does not contain leading zeros except for the zero itself.

```
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
var addBinary = function(a, b) {
    var result = "", carry = 0;

      while(a || b || carry){
        let sum = +a.slice(-1) + +b.slice(-1) + carry; // get last digit from each number and sum 

        if( sum > 1 ){  
          result = sum % 2 + result;
          carry = 1;
        } else {
          result = sum + result;
          carry = 0;
        }

        // trim last digit (110 -> 11)
        a = a.slice(0, -1)
        b = b.slice(0, -1)
      }

      return result;
};
```