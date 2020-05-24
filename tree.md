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

```python
def isSubtree(self, s, t):
    if not t:
        return True
    if not s:
        return False
    if s.val == t.val and self.isSame(s, t):
        return True
    return self.isSubtree(s.left, t) or self.isSubtree(s.right, t)


def isSame(self, s, t):
    if not s and not t:
        return True
    if not s or not t or s.val != t.val:
        return False
    return self.isSame(s.left, t.left) and self.isSame(s.right, t.right)



def isSubtree(self, s: TreeNode, t: TreeNode) -> bool:
    stack = (s, None)
    candidate_roots = None
    while stack:
        node, stack = stack
        if node:
            if node.val == t.val:
                candidate_roots = (node, candidate_roots)

            stack = (node.left, (node.right, stack))
    while candidate_roots:
        candidate_root, candidate_roots = candidate_roots
        stack = (candidate_root, t, None)
        while stack:
            candidate_node, subtree_node, stack = stack
            if candidate_node is None and subtree_node is None:
                continue
            elif candidate_node and subtree_node and candidate_node.val == subtree_node.val:
                stack = (candidate_node.left, subtree_node.left, (
                        candidate_node.right, subtree_node.right, stack))
                break
        else:
            return True
    return False

```

## Kth Smallest Element in a BST

https://leetcode.com/problems/kth-smallest-element-in-a-bst/

```python
def kthSmallest(self, root: TreeNode, k: int) -> int:
    stack = []
    while root or stack:
        while root:
            stack.append(root)
            root = root.left
        root = stack.pop()
        k -= 1
        if k == 0:
            return root.val
        root = root.right

```

## Validate Binary Search Tree

https://leetcode.com/problems/validate-binary-search-tree/

```python
def isValidBST(self, root):
    if not root:
        return True
    stack = [(root, float('-inf'), float('inf')), ]
    while stack:
        root, lower, upper = stack.pop()
        if not root:
            continue
        val = root.val
        if val <= lower or val >= upper:
            return False
        stack.append((root.right, val, upper))
        stack.append((root.left, lower, val))
    return True

```

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
