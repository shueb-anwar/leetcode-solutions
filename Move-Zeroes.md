# Move Zeroes

Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

**Note** that you must do this in-place without making a copy of the array.

 

**Example 1**:
```
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```
**Example 2:**
```
Input: nums = [0]
Output: [0]
``` 

**Constraints:**

- `1 <= nums.length <= 104`
- `-231 <= nums[i] <= 231 - 1`
 

**Follow up**: Could you minimize the total number of operations done?

```
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    // var nonZeroPos = 0;
    //     for (var i = 0; i < nums.length; i++) {
    //         if (nums[i] != 0) {
    //             nums[nonZeroPos] = nums[i];
    //             if (nonZeroPos++ < i) {
    //                 nums[i] = 0;
    //             }
    //         }
    //     }
    
    if (nums.length == 0)
            return;
        
    var i = 0;
    for (var j = 1; j < nums.length; j++) {
        if (nums[i] == 0 && nums[j] != 0) {
            [nums[i], nums[j]] = [nums[j], nums[i]]
            i++;
        } else if (nums[i] != 0) {
            i++;
        }
    }
};

```