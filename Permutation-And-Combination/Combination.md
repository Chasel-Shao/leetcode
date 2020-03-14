## 代码

```java
class Solution {
  Stack<Integer> stack = new Stack<Integer>();
  stack.push(0);
  int[] result = new int[4];
  String[] source = new String[] {"a", "b", "c", "d"};
  int k = 3;
  
  String[] nextCombination(String[] source, int k, Stack<Integer> stack, int[] result) {
    int n = source.length;
    while (k != 0 && stack.size() > 0) {
      int index = stack.size() - 1;
      int value = stack.pop();
      while (value < n) {
        result[index++] = value++;
        stack.push(value);
        if (index == k) {
          String[]combination = new String[k];
          for (int i = 0; i < k; i++) {
            combination[i] = source[result[i]];
          }
          return combination;
        }
      }
    }
    return new String[]{};
  }
}
```

```java
List<String> words = new ArrayList<String>(Arrays.asList("a", "b", "c"));
LinkedList<String> tmp =  new LinkedList<String>();
List<List<String>> ans = new ArrayList();
dfs(ans, words, tmp);

public void dfs(List<List<String>> ans, List<String> words, LinkedList<String> tmp){
		if (tmp.size() == 2) {
			ans.add(new LinkedList<>(tmp));
			return;
		}
		for (String str : words) {
			if (!tmp.contains(str)) {
				tmp.add(str);
				dfs(ans, words, tmp);
				tmp.removeLast();
			}
		}
	}

```

