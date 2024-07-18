# Breadth First Search

## Implementation
```java
package DSA.Trees;

import java.util.LinkedList;
import java.util.Queue;
import DSA.Node.TreeNode;

public class BreadthFirstSearch {

    public void BFS(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);

        while (!queue.isEmpty()) {
            int size = queue.size();

            for (int i = 0; i < size; i++) {
                TreeNode currentNode = queue.poll();
                if (currentNode.left != null) {
                    queue.add(currentNode.left);
                }
                if (currentNode.right != null) {
                    queue.add(currentNode.right);
                }
                System.out.println(currentNode.val);
            }
        }
    }
}
```

## Chapter Recap

* Breadth-first search tells you if there’s a path from A to B.

* If there’s a path, breadth-first search will find the shortest path.

* If you have a problem like “find the shortest X,” try modeling your problem as a graph and use breadth-first search to solve it.

* A directed graph has arrows, and the relationship follows the direction of the arrow (rama → adit means “rama owes adit money”).

* Undirected graphs don’t have arrows, and the relationship goes both ways (ross— rachel means “ross dated rachel and rachel dated ross”).

* Queues are FIFO (first in, first out).

* Stacks are LIFO (last in, first out).

* You need to check people in the order they were added to the search list, so the search list needs to be a queue. Otherwise, you won’t get the shortest path.

* Once you check someone, make sure you don’t check them again. Otherwise, you might end up in an infinite loop.
