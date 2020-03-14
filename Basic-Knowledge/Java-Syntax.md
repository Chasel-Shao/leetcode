## Data Structure

### PriorityQueue

```java
Queue<ListNode> heap = new PriorityQueue<ListNode>((a, b) -> a.val - b.val);

private Comparator<ListNode> ListNodeComparator = new Comparator<ListNode>() {
	public int compare(ListNode left, ListNode right) {
		return left.val - right.val;
	}
};
Queue<ListNode> heap = new PriorityQueue<ListNode>(lists.size(), ListNodeComparator);
```

### Min Heap

```java
PriorityQueue<Integer> q =  new PriorityQueue<Integer>();
```

### Max Heap

```java
PriorityQueue<Integer> q =  new PriorityQueue<Integer>(Collections.reverseOrder());
```

### Stack

```java
Deque<TreeNode> stack = new ArrayDeque<>();
```

### Comparator

```java

```

### Array

```java
int[] candies = new int[ratings.length];
Arrays.fill(candies, 1);
int[] copy = Arrays.copyOfRange(arr, 2, 6); 
int[] perm = Arrays.copyOf(nums, nums.length);
Arrays.sort(chs);
```

### ArrayList

```java
Collections.reverse(wordList);
Collections.swap(nums, first, i);

# 初始化方法 #1
  ArrayList<Type> obj = new ArrayList<Type>(Arrays.asList(Object o1, Object o2, Object o3, ....so on));
# 初始化方法 #2
ArrayList<T> obj = new ArrayList<T>() {{
    add(Object o1);
    add(Object o2);
}};
# 初始化方法 #3
ArrayList<T> obj = new ArrayList<T>();
obj.add("o1");
obj.add("o2");
# 初始化方法 #4
ArrayList<T> obj = new ArrayList<T>(Collections.nCopies(count,element));
```

### TreeMap

```java

```

### TreeSet

```java

```

### Queue

```java
Queue<Integer> toVisit = new ArrayDeque<>();
```

### BitSet

```java
BitSet hasCycle = new BitSet(1);
```

### Pair

```java
import javafx.util.Pair;

```

### String

```java
new StringBuffer(word).reverse().toString()
  
# indexOf() / lastIndexOf()
String str ="We are students";
int size = str.indexOf("a");  // 变量size的值是3
# charAt()
String str = "hello word";
char mychar =  str.charAt(5);  // mychar的结果是w
# substring(int beginIndex)
String str = "Hello word";
String substr = str.substring(3); //获取字符串，此时substr值为lo word
# substring(int beginIndex,  int endIndex)
String str = "Hello word";
String substr = str.substring(0,3); //substr的值为hel
# trim()
# replace()
String str= "address";
String newstr = str.replace("a", "A");// newstr的值为Address
# startsWith(String prefix)
# endsWith(String suffix)
# equals(String otherstr)
# equalsIgnoreCase(String otherstr)
# str.toLowerCase();
# str.toUpperCase();
# str.split(String sign);
# str.split(String sign, in limit)；
```

### Character

```java
 int d = Character.getNumericValue('0') // 0
```

### LinkedHashMap

```java
LinkedHashMap<Character, Integer> hashmap = new LinkedHashMap<Character, Integer> (k + 1);
Map.Entry<Character, Integer> leftmost = hashmap.entrySet().iterator().next();
hashmap.remove(leftmost.getKey());
```

### Regx

```java
import java.util.regex.Pattern;
class Solution {
  String chunkIPv4 = "([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])";
  Pattern pattenIPv4 =
          Pattern.compile("^(" + chunkIPv4 + "\\.){3}" + chunkIPv4 + "$");

  String chunkIPv6 = "([0-9a-fA-F]{1,4})"; // {4} 无法通过,ipv6可以为单个字符
  Pattern pattenIPv6 =
          Pattern.compile("^(" + chunkIPv6 + "\\:){7}" + chunkIPv6 + "$");

  public String validIPAddress(String IP) {
    if (pattenIPv4.matcher(IP).matches()) return "IPv4";
    return (pattenIPv6.matcher(IP).matches()) ? "IPv6" : "Neither";
  }
}
```

