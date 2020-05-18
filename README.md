# Merge Two Sorted Linked Lists
# https://leetcode.com/problems/merge-two-sorted-lists

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.
```
Example:

Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

# Implementation :

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(l1 == null || l2 == null)
            return l1 == null ? l2 : l1;
        
        ListNode p1 = l1, p2 = l2;
        ListNode head = null;
        ListNode prev = null;
        ListNode node = null;
        while(p1 != null && p2 != null) {
            if(p1.val <= p2.val) {
                node = new ListNode(p1.val);
                p1 = p1.next;
            } else {
                node = new ListNode(p2.val);
                p2 = p2.next;
            }
            if(head == null)
                head = node;
            if(prev != null)
                prev.next = node;
            prev = node;
        }
        while(p1 != null){
            node = new ListNode(p1.val);
            prev.next = node;
            prev = node;
            p1 = p1.next;
        }
        while(p2 != null) {
            node = new ListNode(p2.val);
            prev.next = node;
            prev = node;
            p2 = p2.next;
        }
        
       return head; 
    }
}
```

