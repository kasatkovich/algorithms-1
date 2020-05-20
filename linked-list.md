# Linked List

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

def reverseList(self, head):
        prev = None
        curr = head
        while (curr != None):
            nextT = curr.next
            curr.next = prev
            prev = curr
            curr = nextT
        return prev    

## Middle Of The Linked List

https://leetcode.com/problems/middle-of-the-linked-list/

def middleNode(self, head):
        once = twice = head
        while twice and twice.next:
            once = once.next
            twice = twice.next.next
        return once    

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

    def hasCycle(self, head):
        if not head or not head.next: 
            return False        
        slow, fast = head, head.next
        while slow != fast:
            if not fast or not fast.next:
                return False
            slow, fast = slow.next, fast.next.next
        return True 

## Reorder List

https://leetcode.com/problems/reorder-list/

## Intersection Of Two Linked List

https://leetcode.com/problems/intersection-of-two-linked-lists/

## Sort List

https://leetcode.com/problems/sort-list/
