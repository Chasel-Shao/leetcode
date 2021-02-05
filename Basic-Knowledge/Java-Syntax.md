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

PriorityQueue<Map.Entry<String, Integer>> pq = new PriorityQueue<>((a, b) -> (a.getValue() == b.getValue() ? a.getKey().compareTo(b.getKey()) : b.getValue() - a.getValue()));
pq.addAll(curr.counts.entrySet());
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
Stack<TreeNode> stack = new Stack();
Deque<TreeNode> stack = new LinkedList<>();

ArrayDeque
add(Element e) 
clear() 
getFirst():
getLast():
isEmpty(): 
pollFirst() :
pollLast()
peek() 
peekFirst() 
pollLast() 
pop() 
push(Element e)
remove() 
removeFirst()
removeLast() 
  
## To String
Stack<Character> ans = new Stack();
String.valueOf(ans);
```

### Queue

```java
Queue<Integer> toVisit = new ArrayDeque<>();
Queue<String> data_list = new LinkedList<String>(Arrays.asList(data_array));

Deque<int[]> queue = new LinkedList<>();
queue.pollFirst()
queue.offerLast()
```

### Comparator

```java
Arrays.sort(asStrs, new LargerNumberComparator());

private class LargerNumberComparator implements Comparator<String> {
    @Override
    public int compare(String a, String b) {
      String order1 = a + b;
      String order2 = b + a;
      return order2.compareTo(order1);
    }
  }
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
Arrays.sort(words, (a, b) -> a.length() - b.length());

int[] nums;
int sum  = Arrays.stream(nums).sum();

int[] snums = nums.clone();

## List => Array
List<int[]> ans = new ArrayList();
ans.toArray(new int[ans.size()][]);

## ToString
String s = Arrays.deepToString(board).replaceAll("\\[|\\]|,|\\s", "");
## Join ToString
String.join(",", list);

## Sort
int[][] intervals
Arrays.sort(intervals, (i1, i2) -> Integer.compare(i1[0], i2[0]));

# Int to char[]
int num = 33212;
char[] A = Integer.toString(num).toCharArray();

## Equal
char[] str1 = s.toCharArray();
char[] str2 = t.toCharArray();
Arrays.sort(str1);
Arrays.sort(str2);
Arrays.equals(str1, str2);

## Binary Search
Arrays.binarySearch(arr, key)
Arrays.binarySearch(arr, fromIndex, toIndex, key)

The array must be sorted (as by the Arrays.sort() method) prior to making this call. If it is not sorted, the results are undefined. If the array contains multiple elements with the specified value, there is no guarantee which one will be found.
index of the search key, if it is contained in the array; otherwise, (-(insertion point) – 1).
Arrays.binarysearch() vs Collections.binarysearch()
Arrays.binarysearch() works for arrays which can be of primitive data type also. Collections.binarysearch() works for objects Collections like ArrayList and LinkedList.
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

## Binary Search
 List al = new ArrayList(); 
al.add(100); 
al.add(50); 
al.add(30); 
al.add(10); 
al.add(2); 
// The last parameter specifies the comparator method 
index = Collections.binarySearch(al, 13); 
// used for sorting. Searching an int key in a list sorted in descending order.
int index = Collections.binarySearch(al, 50,  Collections.reverseOrder()); 
```

### HashMap

```
## equal
pCount.equals(sCount)
```



### TreeMap

```java
boolean containsKey(Object key): Returns true if this map contains a mapping for the specified key.
boolean containsValue(Object value): Returns true if this map maps one or more keys to the specified value.
Object firstKey(): Returns the first (lowest) key currently in this sorted map.
Object get(Object key): Returns the value to which this map maps the specified key.
Object lastKey(): Returns the last (highest) key currently in this sorted map.
Object remove(Object key): Removes the mapping for this key from this TreeMap if present.
void putAll(Map map): Copies all of the mappings from the specified map to this map.
Set entrySet(): Returns a set view of the mappings contained in this map.
int size(): Returns the number of key-value mappings in this map.
Collection values(): Returns a collection view of the values contained in this map.
Object clone(): The method returns a shallow copy of this TreeMap.
void clear(): The method removes all mappings from this TreeMap and clears the map.
SortedMap headMap(Object key_value): The method returns a view of the portion of the map strictly less than the parameter key_value.
Set keySet(): The method returns a Set view of the keys contained in the treemap.
Object put(Object key, Object value): The method is used to insert a mapping into a map
SortedMap subMap((K startKey, K endKey): The method returns the portion of this map whose keys range from startKey, inclusive, to endKey, exclusive.
                 
floorKey()
ceilingKey()
```

### TreeSet

```java
TreeSet<String> ans = new TreeSet<>();
return new ArrayList<>(ans);
// convert to string array
TreeSet<String> set = new TreeSet<>();
set.toArray(new String[0]);

void add(Object o)
boolean addAll(Collection c)
void clear()
boolean contains(Object o)
Object first()
Object last()
SortedSet headSet(Object toElement)
SortedSet tailSet(Object fromElement)
boolean isEmpty()
int size()
boolean remove(Object o)
ceiling​(E e): This method returns the least element in this set greater than or equal to the given element, or null if there is no such element.
floor​(E e): This method returns the greatest element in this set less than or equal to the given element, or null if there is no such element.
pollFirst​()
pollLast​()
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
String reversed = new StringBuilder(combined).reverse().toString();

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

boolean startsWith(String str): It returns true if the String str is a prefix of the String.
boolean startsWith(String str, index fromIndex)
  
public int indexOf(int char)
public int indexOf(int char, int fromIndex)
public int lastIndexOf(int ch)
public int lastIndexOf(int ch, int before)
  
(n1 == n2) ? String.valueOf(n1) : String.format("%d->%d", n1, n2);
```

### Character

```java
 int d = Character.getNumericValue('0') // 0
 Character.isLetterOrDigit(s.charAt(l))
 Character.toLowerCase(s.charAt(l)
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

### HashSet

```java
boolean    add(E e) //如果 set 中尚未存在指定的元素，则添加此元素（可选操作）。
boolean    addAll(Collection<? extends E> c) //如果 set 中没有指定 collection 中的所有元素，则将其添加到此 set 中（可选操作）。
void    　　clear() //移除此 set 中的所有元素（可选操作）。
boolean    contains(Object o) //如果 set 包含指定的元素，则返回 true。
boolean    containsAll(Collection<?> c) //如果此 set 包含指定 collection 的所有元素，则返回 true。
boolean    equals(Object o) //比较指定对象与此 set 的相等性。
int    　　 hashCode() //返回 set 的哈希码值。
boolean    isEmpty() //如果 set 不包含元素，则返回 true。
Iterator<E>    iterator() //返回在此 set 中的元素上进行迭代的迭代器。
boolean    remove(Object o) //如果 set 中存在指定的元素，则将其移除（可选操作）。
boolean    removeAll(Collection<?> c) //移除 set 中那些包含在指定 collection 中的元素（可选操作）。
boolean    retainAll(Collection<?> c) //仅保留 set 中那些包含在指定 collection 中的元素（可选操作）。
int    　　 size() //返回 set 中的元素数（其容量）。
Object[]   toArray() //返回一个包含 set 中所有元素的数组。
<T> T[]    toArray(T[] a) //返回一个包含此 set 中所有元素的数组；返回数组的运行时类型是指定数组的类型。

String[] str = new String[] {"123"};
HashSet<String> set = new HashSet<>(Arrays.asList(str));
```

### LinkedHashMap

```java
LinkedHashMap<Character, Integer> hashmap = new LinkedHashMap<Character, Integer>(k+1);
```

