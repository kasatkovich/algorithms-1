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

## Sort List

https://leetcode.com/problems/sort-list/

def sortList(self, head):
        if (head == None or head.next == None):
            return head
        slow = head
        fast = head
        while( fast.next != None and fast.next.next != None):
            slow = slow.next
            fast = fast.next.next
        right = self.sortList(slow.next)
        slow.next = None
        left = self.sortList(head)
        result = ListNode(None)
        previous = result
        while( right != None and left != None):
            if left.val < right.val:
                previous.next = left
                previous = left
                left = left.next
            else:
                previous.next = right
                previous = right
                right = right.next
        if left != None:
            previous.next = left
        elif right != None:
            previous.next = right
        return result.next
