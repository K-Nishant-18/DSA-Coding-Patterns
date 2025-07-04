# Topological Sort Pattern in Java

## Overview
The Topological Sort pattern orders nodes in a directed acyclic graph (DAG) based on dependencies.

## Use Cases
- Course scheduling with prerequisites.
- Task scheduling with dependencies.

## Approach
1. Use DFS or Kahn’s algorithm.
2. Process nodes with no incoming edges, updating dependencies.

## Example Problem: Course Schedule II
Find a valid order of courses to take given prerequisites.

### Java Implementation
```java
import java.util.*;

public class CourseScheduleII {
    public static int[] findOrder(int numCourses, int[][] prerequisites) {
        List<Integer>[] graph = new List[numCourses];
        for (int i = 0; i < numCourses; i++) graph[i] = new ArrayList<>();
        int[] inDegree = new int[numCourses];
        for (int[] prereq : prerequisites) {
            graph[prereq[1]].add(prereq[0]);
            inDegree[prereq[0]]++;
        }
        Queue<Integer> queue = new LinkedList<>();
        for (int i = 0; i < numCourses; i++) if (inDegree[i] == 0) queue.offer(i);
        int[] result = new int[numCourses];
        int index = 0;
        while (!queue.isEmpty()) {
            int course = queue.poll();
            result[index++] = course;
            for (int next : graph[course]) {
                if (--inDegree[next] == 0) queue.offer(next);
            }
        }
        return index == numCourses ? result : new int[]{};
    }
}
```

### Explanation
- **Time Complexity**: O(V + E), where V is vertices, E is edges.
- **Space Complexity**: O(V + E).

## Navigation
[Back to README](README.md)