# Tree

+[Binary Tree Inorder Traversal](#binary-tree-inorder-traversal)
+[Symmetric Tree](#symmetric-tree)
+[Maximum Depth of Binary Tree](#maximum-depth-of-binary-tree)
+[Same Tree](#same-tree)
+[Invert Binary Tree](#invert-binary-tree)
+[Path Sum](#path-sum)
+[Binary Tree Level Order Traversal](#binary-tree-level-order-traversal)
+[Subtree of Another Tree](#subtree-of-another-tree)
+[Kth Smallest Element in a BST](#kth-smallest-element-in-a-bst)
+[Validate Binary Search Tree](#validate-binary-search-tree)
+[Binary Search Tree Iterator](#binary-search-tree-iterator)

## Binary Tree Inorder Traversal

https://leetcode.com/problems/binary-tree-inorder-traversal/

```python
def helper(self, root, res):
    if not root:
        return None
    if root.left:
        self.helper(root.left, res)
    res.append(root.val)
    if root.right:
        self.helper(root.right, res)


def inorderTraversal(self, root):
    res = []
    self.helper(root, res)
    return res

```

## Symmetric Tree

https://leetcode.com/problems/symmetric-tree/

```python
def isSymmetric(self, root: TreeNode) -> bool:
    if root is None:
        return True
    return self.isSymetricalHelper(root.left, root.right)


def isSymetricalHelper(self, left: TreeNode, right: TreeNode):
    if not left and not right:
        return True
    elif not left or not right or left.val != right.val:
        return False
    return self.isSymetricalHelper(left.left, right.right) and self.isSymetricalHelper(left.right, right.left)


def isSymmetric(self, root: TreeNode) -> bool:
    if root:
        queue = deque([root, root])
        while queue:
            val1 = queue.pop()
            val2 = queue.pop()

            if not val1 and not val2:
                continue
            if not val1 or not val2:
                return False
            if val1.val != val2.val:
                return False
            queue.append(val1.left)
            queue.append(val2.right)
            queue.append(val1.right)
            queue.append(val2.left)

        return True
    return True

```

## Maximum Depth of Binary Tree

https://leetcode.com/problems/maximum-depth-of-binary-tree/

```python
def maxDepth(self, root):
    if not root:
        return 0
    return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))

```

## Same Tree

https://leetcode.com/problems/same-tree/

```python

def isSameTree(self, p, q):
    if not p and not q:
        return True
    if not q or not p:
        return False
    if p.val != q.val:
        return False
    return self.isSameTree(p.right, q.right) and self.isSameTree(p.left, q.left)

def isSameTree(self, p, q):

    def check_nodes(p, q):
        if not p and not q:
            return True
        if not q or not p:
            return False
        if p.val != q.val:
            return False
        return True

    deq = deque([(p, q), ])
    while deq:
        p, q = deq.popleft()
        if not check_nodes(p, q):
            return False
        if p:
            deq.append((p.left, q.left))
            deq.append((p.right, q.right))

    return True

```

## Invert Binary Tree
https://leetcode.com/problems/invert-binary-tree/

```python
def invertTree(self, root):
    if not root:
        return

    root.left, root.right = root.right, root.left

    self.invertTree(root.right)
    self.invertTree(root.left)

    return root

```

## Path Sum

https://leetcode.com/problems/path-sum/

## Binary Tree Level Order Traversal

https://leetcode.com/problems/binary-tree-level-order-traversal/

## Subtree of Another Tree

https://leetcode.com/problems/subtree-of-another-tree/

## Kth Smallest Element in a BST

https://leetcode.com/problems/kth-smallest-element-in-a-bst/

## Validate Binary Search Tree

https://leetcode.com/problems/validate-binary-search-tree/

## Binary Search Tree Iterator

https://leetcode.com/problems/binary-search-tree-iterator/

```python
class BSTIterator:
    def __init__(self, root: TreeNode):
        self.nodes_sorted = []
        self.index = -1
        self._inorder(root)


    def _inorder(self, root):
        if not root:
            return
        self._inorder(root.left)
        self.nodes_sorted.append(root.val)
        self._inorder(root.right)


    def next(self) -> int:
        self.index += 1
        return self.nodes_sorted[self.index]


    def hasNext(self) -> bool:
        return self.index + 1 < len(self.nodes_sorted)

```
