# Intervals

+[Reverse Linked List](#reverse-linked-list)
+[Middle Of The Linked List](#middle-of-the-linked-list)
+[Palindrome Linked List](#palindrome-linked-list)
+[Merge Two Sorted List](#merge-two-sorted-list)
+[Remove Nth Node From End Of The List](#remove-nth-node-from-end-of-the-list)
+[Linked List Cycle II](#linked-list-cycle-ii)
+[Linked List Cycle](#linked-list-cycle)
+[Reorder List](#reorder-list)
+[Intersection Of Two Linked List](#intersection-of-two-linked-list)
+[Sort List](#sort-list)

## Reverse Linked List

https://leetcode.com/problems/reverse-linked-list/

## Middle Of The Linked List

https://leetcode.com/problems/middle-of-the-linked-list/

## Palindrome Linked List

https://leetcode.com/problems/palindrome-linked-list/

## Merge Two Sorted List

https://leetcode.com/problems/merge-two-sorted-lists/

def mergeTwoLists(self, l1, l2):
        if not l1:
            return l2
        if not l2:
            return l1
        if (l1.val <= l2.val):   
            l1.next = self.mergeTwoLists(l1.next,l2)
            return l1
        else:   
            l2.next = self.mergeTwoLists(l1,l2.next)
            return l2  

## Remove Nth Node From End Of The List

https://leetcode.com/problems/remove-nth-node-from-end-of-list/

## Linked List Cycle II

https://leetcode.com/problems/linked-list-cycle-ii/

## Linked List Cycle 

https://leetcode.com/problems/linked-list-cycle/

## Reorder List

https://leetcode.com/problems/reorder-list/

## Intersection Of Two Linked List

https://leetcode.com/problems/intersection-of-two-linked-lists/

## Sort List

https://leetcode.com/problems/sort-list/
