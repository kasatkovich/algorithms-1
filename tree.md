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

## Maximum Depth of Binary Tree

https://leetcode.com/problems/maximum-depth-of-binary-tree/

## Same Tree

https://leetcode.com/problems/same-tree/



## Invert Binary Tree
https://leetcode.com/problems/invert-binary-tree/

## Path Sum

https://leetcode.com/problems/path-sum/

## Binary Tree Level Order Traversal

https://leetcode.com/problems/binary-tree-level-order-traversal/

## Subtree of Another Tree

https://leetcode.com/problems/subtree-of-another-tree/

```python
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

## Validate Binary Search Tree

https://leetcode.com/problems/validate-binary-search-tree/

## Binary Search Tree Iterator

https://leetcode.com/problems/binary-search-tree-iterator/
