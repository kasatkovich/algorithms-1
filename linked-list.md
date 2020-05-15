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

def getIntersectionNode(self, headA, headB):
        s1 = headA
        s2 = headB
        len1 = 0
        len2 = 0
        while s1 != None:
            len1 = len1 + 1
            s1 = s1.next
        while s2 != None:
            len2 = len2 + 1
            s2 = s2.next   
        s1 = headA
        s2 = headB
        if len1 <= len2:
            for i in range(len2 - len1):
                s2 = s2.next
        if len2 < len1:
            for i in range(len1 - len2):
                s1 = s1.next     
        while s1 != None:
            if s1 == s2:
                return s1
            s1 = s1.next
            s2 = s2.next
        return None  

## Sort List

https://leetcode.com/problems/sort-list/
