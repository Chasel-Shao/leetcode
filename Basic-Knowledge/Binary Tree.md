## Binary Tree

### 1. Inorder

Get the elements in order

##### 1.1 Recursion

```java
public void inorder(TreeNode root) {
  inorder(root.left);
  // do something with root.val
  inorder(root.right);
}
```

##### 1.2 Iteration with stack

```java
public void inorder(TreeNode root) {
  LinkedList<TreeNode> stack = new LinkedList<TreeNode>();
  
  while (true) {
    while (root != null) {
      stack.add(root);
      root = root.left;
    }
    
    root = stack.removeLast();
    
    // do something with root.val
    
    root = root.right;
  }
}
```

##### 1.3 Iteration leaf node with stack

```java
public void inorder(TreeNode root) {
  LinkedList<TreeNode> stack = new LinkedList();
  stack.add(root);
  while (!stack.isEmpty()) {
    node = stack.pollLast();
    
    if (node.left == null && node.right == null) {
      // do sth with leaf node
    } 
    
    if (node.left != null) {
      // do sth with node.left.val
      stack.add(node.left);
    }
    
    if (node.right != null) {
      // do sth with node.left.val
      stack.add(node.right);
    }
    
  }
}
```



