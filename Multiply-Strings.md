#  Multiply Strings

Given two non-negative integers `num1` and `num2` represented as strings, return the product of `num1` and `num2`, also represented as a string.

**Note**: You must not use any built-in BigInteger library or convert the inputs to integer directly.

 

**Example 1:**
```
Input: num1 = "2", num2 = "3"
Output: "6"
```

**Example 2:**
```
Input: num1 = "123", num2 = "456"
Output: "56088"
```

*Constraints:**

- `1 <= num1.length, num2.length <= 200`
- `num1` and `num2` consist of digits only.
- Both `num1` and `num2` do not contain any leading zero, except the number `0` itself.

```
/**
 * @param {string} num1
 * @param {string} num2
 * @return {string}
 */
var multiply = function(num1, num2) {
  let result = new Array(num1.length + num2.length).fill(0);

  for (let i = num1.length - 1; i >= 0; i--) {
    let index = num2.length + i;
    let carry = 0;
    for (let j = num2.length - 1; j >= 0; j--) {
      let value = num1[i] * num2[j] + carry + result[index];
      result[index] = value % 10;
      carry = (value - result[index]) / 10;
      index--;
    }
    result[index] += carry;
  }
  if (result[0] === 0) {
    while (result[0] === 0 && result.length !== 1) {
      result.shift();
    }
  }
  return result.join("").toString();
}

```
