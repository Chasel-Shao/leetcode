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

private Queue<Long> small = new PriorityQueue(Collections.reverseOrder()),
private Queue<Long> large = new PriorityQueue();


PriorityQueue<Integer> minHeap = new PriorityQueue<Integer>();
PriorityQueue<Integer> maxHeap = new PriorityQueue<Integer>(1, new Comparator<Integer>(){
  @Override
  public int compare(Integer x, Integer y) {
    return y - x;
  }
});
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
add(Element e) : The method inserts particular element at the end of the deque.
addFirst(Element e) : The method inserts particular element at the start of the deque.
addLast(Element e) : The method inserts particular element at the end of the deque. It is similiar to add() method
clear() : The method removes all deque elements.
size() : The method returns the no. of elements in deque.
contains(Obj) : The method checks whether a deque contains the element or not
Iterator() : The method returns an iterator over the deque.
descendingIterator() : The method returns a reverse order iterator over the deque
element() : The method returns element at the head of the deque
getFirst(): The method returns first element of the deque
getLast(): The method returns last element of the deque
isEmpty(): The method checks whether the deque is empty or not.
offer(Element e) : The method inserts element at the end of deque.
offerFirst(Element e) : The method inserts element at the front of deque.
offerLast(Element e) : The method inserts element at the end of deque.
peek() : The method returns head element without removing it.
peekFirst() : The method returns first element without removing it.
peekLast() : The method returns last element without removing it.
poll() : The method returns head element and also removes it
pollFirst() : The method returns first element and also removes it
pollLast() : The method returns last element and also removes it
pop() : The method pops out an element for stack repesented by deque
push(Element e) : The method pushes an element onto stack repesented by deque
remove() : The method returns head element and also removes it
removeFirst() : The method returns first element and also removes it
removeLast() : The method returns last element and also removes it
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

int[][] points = new int[][] {{1,2}};
int[] p = points[0];
int x = p[0];
int y = p[1];

char[] str1 = s.toCharArray();
char[] str2 = t.toCharArray();
Arrays.sort(str1);
Arrays.sort(str2);
Arrays.equals(str1, str2);
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


public int indexOf(int char)
public int indexOf(int char, int fromIndex)
public int lastIndexOf(int ch)
public int lastIndexOf(int ch, int before)
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

### enum

```java
enum Flag {ROOT, LEFT, RIGHT, MIDDLE};
Flag flag;
flag == Flag.ROOT;
```

### LinkedHashSet

```java
HashMap<Integer, Set<Integer>> idx = new HashMap<Integer, Set<Integer>>();
idx.get(val).add(lst.size());
int remove_idx = idx.get(val).iterator().next();
idx.get(val).remove(remove_idx);
```

