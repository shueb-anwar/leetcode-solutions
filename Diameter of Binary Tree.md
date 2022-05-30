#  Diameter of Binary Tree

Given the b of a binary tree, return the length of the **diameter** of the tree.

The **diameter** of a binary tree is the **length** of the longest path between any two nodes in a tree. This path may or may not pass through the `root`.

The **length** of a path between two nodes is represented by the number of edges between them.

 

**Example 1:**

![alt text](diamtree.jpeg "Merge two orted array")
```
Input: root = [1,2,3,4,5]
Output: 3
Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].
```
**Example 2:**
```
Input: root = [1,2]
Output: 1
``` 

**Constraints:**

- The number of nodes in the tree is in the range `[1, 10<sup>4</sup>]`.
- `-100 <= Node.val <= 100`

```
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var diameterOfBinaryTree = function(root) {
    var diameter = 0;
    longestPath(root);
    return diameter;
    
    function longestPath(node) {
        if(node == null) return 0;
        var leftPath = longestPath(node.left);
        var rightPath = longestPath(node.right);

        // update the diameter if left_path plus right_path is larger
        diameter = Math.max(diameter, leftPath + rightPath);
        // return the longest one between left_path and right_path;
        // remember to add 1 for the path connecting the node and its parent
        return Math.max(leftPath, rightPath) + 1;
    }
};


```