# Tree Breadth-First Search (BFS) Pattern in Java

## Overview
The Tree BFS pattern processes tree nodes level by level using a queue.

## Use Cases
- Level-order traversal.
- Find minimum depth of a binary tree.

## Approach
1. Use a queue to store nodes at the current level.
2. Process each level and enqueue children for the next level.

## Example Problem: Level Order Traversal
Perform a level-order traversal of a binary tree.

### Java Implementation
```java
class TreeNode {
    int val;
    TreeNode left, right;
    TreeNode(int val) { this.val = val; }
}

public class LevelOrderTraversal {
    public static List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) return result;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        while (!queue.isEmpty()) {
            int levelSize = queue.size();
            List<Integer> currentLevel = new ArrayList<>();
            for (int i = 0; i < levelSize; i++) {
                TreeNode node = queue.poll();
                currentLevel.add(node.val);
                if (node.left != null) queue.offer(node.left);
                if (node.right != null) queue.offer(node.right);
            }
            result.add(currentLevel);
        }
        return result;
    }
}
```

### Explanation
- **Time Complexity**: O(n).
- **Space Complexity**: O(w), where w is the maximum width.

## Navigation
[Back to README](README.md)