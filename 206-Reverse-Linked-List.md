## Java
### Reverse a singly linked list.
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
    public ListNode reverseList(ListNode head) {
        if(head == null){
            return null;
        }
        if(head.next == null){
            return head;
        }
        ListNode next = head.next;
        ListNode node = reverseList(next);
        next.next = head;
        head.next = null;
        return node;
    }
}
```