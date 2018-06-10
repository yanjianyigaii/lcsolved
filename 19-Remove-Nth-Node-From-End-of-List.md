###
Given a linked list, remove the n-th node from the end of list and return its head.
```
Example:

Given linked list: 1->2->3->4->5, and n = 2.
```
After removing the second node from the end, the linked list becomes 1->2->3->5.
Note:

Given n will always be valid.

Follow up:

Could you do this in one pass?
###

Javascript

```
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} n
 * @return {ListNode}
 */

var removeNthFromEnd = function(head, n) {
    if(head.next == null && n==1){
        return null;
    }
    find(head, n);
    return head;
};
var find = function(node, n){
    if(node == null){
        return 0;
    }
    var current = find(node.next, n)+1;
    if(current === n && n===1){
        return current;
    }
    if(current ==2 && n==1){
        node.next = null;
    }
    if(current == n){
        var next = node.next;
        node.next = next.next;
        node.val = next.val;
    }
    return current;
};
```