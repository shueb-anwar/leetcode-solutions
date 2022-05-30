#  Merge Two Sorted Lists

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists in a one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

**Example 1:**

![alt text](merge_ex1.jpeg "Merge two orted array")
```
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```
**Example 2:**
```
Input: list1 = [], list2 = []
Output: []
```
**Example 3:**
```
Input: list1 = [], list2 = [0]
Output: [0]
``` 

**Constraints:**

- The number of nodes in both lists is in the range `[0, 50]`.
- `-100 <= Node.val <= 100`
- Both `list1` and `list2` are sorted in non-decreasing order.

```
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} list1
 * @param {ListNode} list2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    let dummy = { val: -1, next: null};
    let prev = dummy
    
    while (l1 !== null || l2 !== null) {
        if ((l1 && l2 && l1.val <= l2.val) || (!l2 && l1)) {
            prev.next = l1;
            l1 = l1.next;
        } else {
            prev.next = l2;
            l2 = l2.next;
        }
        
        prev = prev.next;
    }
    
    return dummy.next;
};
```