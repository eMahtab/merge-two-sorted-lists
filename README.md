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
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(l1 == null || l2 == null)
            return l1 == null ? l2: l1;
        ListNode head = null;
        ListNode prev = null;
        while(l1 != null && l2 != null){
            ListNode node = null;
            if(l1.val < l2.val){
                node = new ListNode(l1.val);
                l1 = l1.next;
            }else{
                node = new ListNode(l2.val);
                l2 = l2.next;
            }
            
            if(head == null){
                head = node;
            }
            if(prev != null){
                prev.next = node;
            }
            prev = node;
                            
        }
        while(l1 != null){
            ListNode x = new ListNode(l1.val);
            prev.next = x;
            prev = x;
            l1 = l1.next;
        }
        while(l2 != null){
            ListNode y = new ListNode(l2.val);
            prev.next = y;
            prev = y;
            l2 = l2.next;
        }
        
        return head;
    }
}
```

