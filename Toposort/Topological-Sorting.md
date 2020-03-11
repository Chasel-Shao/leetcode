## Topological Sorting

----
## 题目地址

[https://www.lintcode.com/problem/topological-sorting/description](https://www.lintcode.com/problem/topological-sorting/description)

## 题目描述

```text
Given an directed graph, a topological order of the graph nodes is defined as follow:

For each directed edge A -> B in graph, A must before B in the order list.
The first node in the order can be any node in the graph with no nodes direct to it.
Find any topological order for the given graph.
```

## 代码

```java
class Graph {
  private int V;
  private LinkedList<Integer> adj[];

  Graph(int v) {
    V = v;
    adj = new LinkedList[v];
    for (int i = 0; i < v; i++) {
      adj[i] = new LinkedList();
    }

    void addEdge(int v, int w) { adj[v].add(w); }

    void topologicalSortUtil(int v, boolean visited[], Stack stack) {
      visited[v] = true;
      Integer i;

      Iterator<Integer> it = adj[v].iterator();
      while (it.hasNext()) {
        i = it.next();
        if (!visited[i]) {
          topologicalSortUtil(i, visited, stack);
        }
      }

      stack.push(new Integer(v));
    }

    void topologicalSort() {
      Stack stack = new Stack();

      boolean visited[] = new boolean[V];
      for (int i = 0; i < V; i++) {
        visited[i] = false;
      }

      for (int i = 0; i < V; i++) {
        if (visited[i] == false) {
          topologicalSortUtil(i, visited, stack);
        }
      }

      while (stack.empty() == false) {
        System.out.print(stack.pop() + " ");
      }

    }

  }
}
```

