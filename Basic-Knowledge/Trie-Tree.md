# Trie Tree

```java
public class Trie {
    final int APHABET_SIZE = 26;
  TrieNode root;

  class TrieNode {
    TrieNode[] children = new TrieNode[APHABET_SIZE];
    boolean isEndOfWord;

    TrieNode() {
      isEndOfWord = false;
      for (int i = 0; i < APHABET_SIZE; i++) 
        children[i] = null;
    }
  };

  void insert(String key) {
    int level;
    int lenght = key.length();
    int index;

    TrieNode pCrawl = root;

    for (level = 0; level < length; level++) {
      index = key.charAt(level) - 'a';
      if (pCrawl.children[index] == null) {
        pCrawl.children[index] = new TrieNode();
      }
      pCrawl = pCrawl.children[index];
    }

    pCrawl.isEndOfWord = true;
  }

  boolean search(String key) {
    int level;
    int length = key.length();
    int index;
    TrieNode pCrawl = root;

    for (level = 0; level < length; level++) {
      index = key.charAt(level) - 'a';
      if (pCrawl.children[index] == null) {
        return false;
      }
      pCrawl = pCrawl.children[index];
    }
  }


}
```

```java
public void insert(String word) {
    TrieNode current = root;

    for (int i = 0; i < word.length(); i++) {
        current = current.getChildren()
          .computeIfAbsent(word.charAt(i), c -> new TrieNode());
    }
    current.setEndOfWord(true);
}

public boolean find(String word) {
    TrieNode current = root;
    for (int i = 0; i < word.length(); i++) {
        char ch = word.charAt(i);
        TrieNode node = current.getChildren().get(ch);
        if (node == null) {
            return false;
        }
        current = node;
    }
    return current.isEndOfWord();
}

public void delete(String word) {
    delete(root, word, 0);
}

private boolean delete(TrieNode current, String word, int index) {
    if (index == word.length()) {
        if (!current.isEndOfWord()) {
            return false;
        }
        current.setEndOfWord(false);
        return current.getChildren().isEmpty();
    }
    char ch = word.charAt(index);
    TrieNode node = current.getChildren().get(ch);
    if (node == null) {
        return false;
    }
    boolean shouldDeleteCurrentNode = delete(node, word, index + 1) && !node.isEndOfWord();

    if (shouldDeleteCurrentNode) {
        current.getChildren().remove(ch);
        return current.getChildren().isEmpty();
    }
    return false;
}
```

