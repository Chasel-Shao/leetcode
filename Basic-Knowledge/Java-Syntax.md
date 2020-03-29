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
Stack<TreeNode> stack = new Stack();

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

int[] nums;
int sum  = Arrays.stream(nums).sum();

int[] snums = nums.clone();
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
```

### TreeSet

```java
void add(Object o): This method will add specified element according to some sorting order in TreeSet. Duplicate entires will not get added.
boolean addAll(Collection c): This method will add all elements of specified Collection to the set. Elements in Collection should be homogeneous otherwise ClassCastException will be thrown. Duplicate Entries of Collection will not be added to TreeSet.
void clear(): This method will remove all the elements.
boolean contains(Object o): This method will return true if given element is present in TreeSet else it will return false.
Object first(): This method will return first element in TreeSet if TreeSet is not null else it will throw NoSuchElementException.
Object last(): This method will return last element in TreeSet if TreeSet is not null else it will throw NoSuchElementException.
SortedSet headSet(Object toElement): This method will return elements of TreeSet which are less than the specified element.
SortedSet tailSet(Object fromElement): This method will return elements of TreeSet which are greater than or equal to the specified element.
SortedSet subSet(Object fromElement, Object toElement): This method will return elements ranging from fromElement to toElement. fromElement is inclusive and toElement is exclusive.
boolean isEmpty(): This method is used to return true if this set contains no elements or is empty and false for the opposite case.
Object clone(): The method is used to return a shallow copy of the set, which is just a simple copied set.
int size(): This method is used to return the size of the set or the number of elements present in the set.
boolean remove(Object o): This method is used to return a specific element from the set.
ceiling​(E e): This method returns the least element in this set greater than or equal to the given element, or null if there is no such element.
descendingIterator​(): This method returns an iterator over the elements in this set in descending order.
descendingSet​(): This method returns a reverse order view of the elements contained in this set.
floor​(E e): This method returns the greatest element in this set less than or equal to the given element, or null if there is no such element.
higher​(E e): This method returns the least element in this set strictly greater than the given element, or null if there is no such element.
lower​(E e): This method returns the greatest element in this set strictly less than the given element, or null if there is no such element.
pollFirst​(): This method retrieves and removes the first (lowest) element, or returns null if this set is empty.
pollLast​(): This method retrieves and removes the last (highest) element, or returns null if this set is empty.
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

```

