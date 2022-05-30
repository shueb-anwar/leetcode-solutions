#  Validate Binary Search Tree

Given the `root` of a binary tree, determine if it is a valid binary search tree (BST).

A **valid BST** is defined as follows:

The left subtree of a node contains only nodes with keys **less than** the node's key.
The right subtree of a node contains only nodes with keys **greater than** the node's key.
Both the left and right subtrees must also be binary search trees.
 

**Example 1**:

![alt text](tree1.jpeg "Merge two orted array")
```
Input: root = [2,1,3]
Output: true
```
**Example 2:**

![alt text](tree2.jpeg "Merge two orted array")
```
Input: root = [5,1,4,null,null,3,6]
Output: false
Explanation: The root node's value is 5 but its right child's value is 4.
``` 

**Constraints**:

- The number of nodes in the tree is in the range `[1, 10<sup>4</sup>]`.
- `-231 <= Node.val <= 231 - 1`

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
 * @return {boolean}
 */
var isValidBST = function(root, maxLeft, minRight) {
    if (!root) {
        return true;
    }
    
    if (root.val <= minRight) {
        return false;
    }
    
    if (root.val >= maxLeft) {
        return false;
    }
    
    return isValidBST(root.left, root.val, minRight) && 
        isValidBST(root.right, maxLeft, root.val);
};
```