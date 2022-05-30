#  Permutations II

Given a collection of numbers, `nums`, that might contain duplicates, return all possible unique permutations **in any order**.

 
**Example 1:**
```
Input: nums = [1,1,2]
Output:
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

**Example 2:**

```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
``` 

**Constraints:**

- `1 <= nums.length <= 8`
- `-10 <= nums[i] <= 10`

```
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permuteUnique = function(nums) {
    const res = []
    
    nums.sort((a, b) => a - b);
    
    const generate = (seq) => {
      if (seq.length === nums.length) {
        res.push([...seq])
        return
      }
      
      for (let i = 0; i < nums.length; i++) {
        const num = nums[i]
        const prev = nums[i - 1]
        
        if (num === null || num === prev) {
          continue
        }
        
        nums[i] = null
        seq.push(num)
        generate(seq)
        seq.pop()
        nums[i] = num
      }
    }
    
    generate([])
  
    return res
};
```