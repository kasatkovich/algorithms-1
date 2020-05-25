# Linked List

+ [Reverse Linked List](#reverse-linked-list)
+ [Middle Of The Linked List](#middle-of-the-linked-list)
+ [Palindrome Linked List](#palindrome-linked-list)
+ [Merge Two Sorted List](#merge-two-sorted-list)
+ [Remove Nth Node From End Of The List](#remove-nth-node-from-end-of-the-list)
+ [Linked List Cycle II](#linked-list-cycle-ii)
+ [Linked List Cycle](#linked-list-cycle)
+ [Reorder List](#reorder-list)
+ [Intersection Of Two Linked List](#intersection-of-two-linked-list)
+ [Sort List](#sort-list)

## Reverse Linked List

https://leetcode.com/problems/reverse-linked-list/

```python
def reverseList(self, head):
    prev = None
    curr = head
    while curr:
        nextT = curr.next
        curr.next = prev
        prev = curr
        curr = nextT
    return prev

```

## Middle Of The Linked List

https://leetcode.com/problems/middle-of-the-linked-list/

```python
def middleNode(self, head):
    once = twice = head
    while twice and twice.next:
        once = once.next
        twice = twice.next.next
    return once

```

## Palindrome Linked List

https://leetcode.com/problems/palindrome-linked-list/

```python
#first solution
def isPalindrome(self, head: ListNode) -> bool:
    self.res = True
    self.node = head

    def hold(root):
        if not root:
            return
        hold(root.next)
        if root.val != self.node.val:
            self.res = False
        self.node = self.node.next
    hold(head)
    return self.res

#second solution
def isPalindrome(self, head: ListNode) -> bool:
    slow = fast = head
    prev = None
    while fast and fast.next:
        fast = fast.next.next
        slow.next, slow, prev = prev, slow.next, slow
    if fast:
        slow = slow.next
    while slow and slow.val == prev.val:
        slow, prev = slow.next, prev.next
    return not slow

```

## Merge Two Sorted List

https://leetcode.com/problems/merge-two-sorted-lists/

```python
#first solution
def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
    head = ListNode(0)
    index = head
    while l1 and l2:
        if l1.val < l2.val:
            index.next = l1
            l1 = l1.next
        else:
            index.next = l2
            l2 = l2.next
        index = index.next
    if not l1:
        index.next = l2
    if not l2:
        index.next = l1
    return head.next

#second solution
def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
    if not l1 and not l2:
        return None
    if not l1:
        return l2
    if not l2:
        return l1
    small, large = (l1, l2) if l1.val < l2.val else (l2, l1)
    head = small
    while small.next:
        if small.next.val > large.val:
            small.next, large = large, small.next
        small = small.next
    small.next = large
    return head

```

## Remove Nth Node From End Of The List

https://leetcode.com/problems/remove-nth-node-from-end-of-list/

```python
def removeNthFromEnd(self, head, n):
    count = 0
    forcount = head
    while forcount:
        count += 1
        forcount = forcount.next
    if n > count:
        n = n-count
    if not head:
        return None
    result = head
    runner = head
    for i in range(n):
        runner = runner.next
    if not runner:
        return result.next
    while (runner.next):
        head = head.next
        runner = runner.next
    head.next = head.next.next
    return result

```        

## Linked List Cycle II

https://leetcode.com/problems/linked-list-cycle-ii/

```python
def detectCycle(self, head):
    slow = head
    fast = head
    found = False
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            found = True
            break
    if not found:
        return None
    slow = head
    while slow != fast:
        slow = slow.next
        fast = fast.next     
    return slow

```

## Linked List Cycle 

https://leetcode.com/problems/linked-list-cycle/

```python
def hasCycle(self, head):
    if not head or not head.next:
        return False
    slow, fast = head, head.next
    while slow != fast:
        if not fast or not fast.next:
            return False
        slow, fast = slow.next, fast.next.next
    return True

```

## Reorder List

https://leetcode.com/problems/reorder-list/

```python
#first solution
def reverseList(self, head):
    prev = None
    curr = head
    while curr:
        nextT = curr.next
        curr.next = prev
        prev = curr
        curr = nextT
    return prev


def reorderList(self, head):
    if not head:
        return head
    fastPoint = head
    slowPoint = head
    while fastPoint and fastPoint.next:
        slowPoint = slowPoint.next
        fastPoint = fastPoint.next.next

    tail = slowPoint
    half = slowPoint
    slowPoint = self.reverseList(half)
    current = None
    while current != tail:
        current = head.next
        head.next = slowPoint
        head = slowPoint
        slowPoint = current

#second solution
def dfs(self, node, head):
    if not node:
        return head
    head = self.dfs(node.next, head)
    if not head:
        return
    if head == node or head.next == node:
        node.next = None
        return
    head_original_next = head.next
    head.next = node
    node.next = head_original_next
    return head_original_next


def reorderList(self, head: ListNode) -> None:
    self.dfs(head, head)

#third solution
def reorderList(self, head):
    s, copy = [], head
    while copy:
        s.append(copy)
        copy = copy.next
    while head:
        if head.next == s[-1]:
            head = head.next
        if head == s[-1]:
            head.next = None
            return
        replace, head.next = head.next, s.pop()
        head.next.next = replace
        head = head.next.next

```

## Intersection Of Two Linked List

https://leetcode.com/problems/intersection-of-two-linked-lists/

```python
def getIntersectionNode(self, headA, headB):
    if not headA or not headB:
        return None
    curNodeA = headA
    curNodeB = headB
    while curNodeA != curNodeB:
        curNodeA = headB if not curNodeA else curNodeA.next
        curNodeB = headA if not curNodeB else curNodeB.next
    return curNodeA

```

## Sort List

https://leetcode.com/problems/sort-list/
```python
def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
    head = ListNode(0)
    index = head
    while l1 and l2:
        if l1.val < l2.val:
            index.next = l1
            l1 = l1.next
        else:
            index.next = l2
            l2 = l2.next
        index = index.next
    if not l1:
        index.next = l2
    if not l2:
        index.next = l1
    return head.next


def middleNode(self, head: ListNode) -> ListNode:
    slowPoint = head
    fastPoint = head
    while fastPoint.next and fastPoint.next.next:
        slowPoint = slowPoint.next
        fastPoint = fastPoint.next.next
    return slowPoint


def sortList(self, head: ListNode) -> ListNode:
    if not head or not head.next:
        return head
    middle = self.middleNode(head)
    right = self.sortList(middle.next)
    middle.next = None
    left = self.sortList(head)
    return self.mergeTwoLists(left, right)

```
