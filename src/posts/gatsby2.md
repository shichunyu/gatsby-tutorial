---
title: "Invert Binary Tree 2"
date: "2020-06-01"
---

# 2020.06.01 Invert Binary Tree - II
tags: #*study/lc challenge#

![Random Image](./gatsby2/img.png)

## BFS Solution
**Runtime:** O(N) where N is the number of nodes in the tree
**Space:** O(N) where N is the number of nodes in the tree

```py
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

from collections import deque

class Solution:
    def invertTree(self, root: TreeNode) -> TreeNode:
        
        if root is None:
            return root
        
        queue = deque()
        queue.append(root)
        
        while queue:
            node = queue.popleft()
            node.left, node.right = node.right, node.left
            
            if node.left is not None:
                queue.append(node.left)
            
            if node.right is not None:
                queue.append(node.right)
                
        return root
```