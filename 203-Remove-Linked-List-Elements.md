###
Remove all elements from a linked list of integers that have value val.

Example
Given: 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, val = 6
Return: 1 --> 2 --> 3 --> 4 --> 5

###
Java

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode removeElements(ListNode head, int val) {
        if(head == null){
            return null;
        }
        while(head != null && head.val == val){
            head = head.next;
        }
        ListNode current = head;
        ListNode parent = null;
        while(current != null){
            if(current.val == val){
                parent.next = current.next;
            }else{
                parent = current;
            }
            current = current.next;
        }
        return head;
    }
}
```