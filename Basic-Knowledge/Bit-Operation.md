# leetcode 位运算

https://www.jianshu.com/p/b93ba9e24f97

## 一、 运算符

- & 与运算： 两个位都是 1 时，结果才为 1，否则为 0
- | 或运算： 两个位都是 0 时，结果才为 0，否则为 1
- ^ 异或运算： 两个位相同则为 0，不同则为 1
- ~ 取反运算：0 则变为 1，1 则变为 0
- << 左移运算：向左进行移位操作，高位丢弃，低位补 0 （每左移一位相当于乘一次2）
- \>> 右移运算：向右进行移位操作，正数右移，高位用 0 补，负数右移，高位用 1 补（每右移一位相当于除一次2）
  - 无符号右移 `>>>`当负数使用无符号右移时，用 0 进行补位

乘以或除以2的幂数

可以用左移<<和右移>>位运算来代替

i << 2, i >> 2

判断一个数的奇偶性

可以用判断二进制最右的一位来代替，最右位是1则是偶数，是0则是奇数。

i & 1

判断一个数是否是2的幂数

x & (x – 1)

将一个数对应的二进制位的最右边的1置为0

x & (x – 1)

将一个数对应的二进制位的最右边的0置为1

x | (x + 1)


将一个数对应的二进制位的最右边的0置为1，其余位全置为0

¬x & (x + 1)

将一个数对应的二进制位的最右边的1置为0，其余位全置为1

¬x | (x – 1)


将一个数对应的二进制位的右尾端连续的1都置为0

x & (x + 1)

将一个数对应的二进制位的右尾端连续的1都置为0，其余位全置为1

¬x | (x + 1)


将一个数对应的二进制位的右尾端连续的0都置为1

x | (x– 1)

将一个数对应的二进制位的右尾端连续的0都置为1，其余位全置为0

¬ x & (x - 1)

将一个数对应的二进制位仅保留最右边的1，其余为全置为0

x & (−(x-1))



### 一些小技巧

- 将数字 A 的第 k 位设置为1：`A = A | (1 << (k - 1))`

- 将数字 A 的第 k 位设置为0：`A = A & ~(1 << (k - 1))`

- 检测数字 A 的第 k 位：`A & (1 << (k - 1)) != 0`

- Extract the lowest set bit 获取数字 A 的最低位：

  ```
  A & -A
  ```

   或者 

  ```
  A & ~(A - 1)
  ```

  - 例如数字 6（110）的最低位对应 2（10）

- 得到 111111..111: `~0`




## 二、 应用场景

^ 异或运算性质：

**（1）交换律**

**（2）结合律（即(a^b)^c == a^(b^c)）**

**（3）对于任何数x，都有x^x=0，x^0=x**

**（4）自反性 A ^ B ^ B = A ^ 0 = A**

**常见应用**：

- **与运算的应用**：（1）清零。如果想将一个单元清零，即使其全部二进制位为0，只要与一个各位都为零的数值相与，结果为零。 （2）取一个数中指定位
- **或运算的应用**： 对一个数的某几位补1
- **异或运算的应用**： 消去一对重复的数（利用上面）， 交换变量等等。
- **取模**： 位运算比加减乘除更加高效。 所以在一些底层的组件例如jdk， redis 中经常用位运算，比如用<< ，>>代替乘除， 用& 代替取模操作。
- **状态压缩和位图**： 位运算可以用压缩存储和表示信息。 每个二进制位有0|1 两种状态， 那一个int32 可以表示出 32种状态。 比如linux中的文件状态中的read ，write， 和执行权限就可以用三个二进制位表示， 7（111）表示有Read的权限，有Write的权限和执行的权限。


```java
String intToString(int x) {
		char[] bytes = new char[4];
		for(int i = 3; i > -1; --i) {
			bytes[3 - i] = (char) (x >> (i * 8) & 0xff);
		}
		return new String(bytes);
	}
  // Decodes bytes string to integer
int stringToInt(String bytesStr) {
    int result = 0;
    for(char b : bytesStr.toCharArray()) {
      result = (result << 8) + (int)b;
    }
    return result;
  }
```



## 三、 例题

**1、** **不使用中间变量交换两数**

```cpp
// 思路： 利用上面提到的异或的结合率 和自反率
// a = (a ^ b) ^ b , b = a ^ b ^ a
void swap(int &a, int &b) {
  a ^= b;
  b ^= a;
  a ^= b;
}
```

**2、** **数组中，只有一个数出现一次，剩下都出现两次，找出出现一次的数 (leetcode - 136)**

```java
    public int singleNumber(int[] nums) {
        int res = 0;
        for(int i = 0; i < nums.length; i++) {
            res = res ^ nums[i];
        }
        return res;
    }
```

**3、 用 O(1) 时间检测整数 n 是否是 2 的幂次 （LintCode - 142）**

```java
/** 思路： 常用技巧：n&(n-1)消去n 的二进制最后一位的1
* 比如3&(3-1) = (11)&(10) = (10) , 
* 如果是2的幂次， 那二进制形式下只有一位是1， 消去后为0
*/    
    public boolean checkPowerOf2(int n) {
        if(n <= 0) return false;
        return (n & (n - 1)) == 0;
    }
```

**4、子集列举 （leetcode - 78 medium）**

**描述：**

Given a set of **distinct** integers, *nums*, return all possible subsets (the power set).

**Note:** The solution set must not contain duplicate subsets.

**Example:**

```text
Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```

**思路：（这道题递归做感觉也很容易理解）**

注意数组中数字唯一，可以把这道题理解成高中数学中的排列组合问题。每个数字有取或不取两种可能性， n个数有2的n次方个子集。 可以用一个正整数二进制表示的第i位是1还是0，代表集合的第i个数取或者不取。类似下图：

```text
0 000 {}
1 001 {1}
2 010 {2}
3 011 {1,2}
4 100 {3}
5 101 {1,3}
6 110 {2,3}
7 111 {1,2,3}
```

A：

```cpp
    vector<vector<int>> subsets(vector<int>& nums) {
        int n = nums.size()
        int p = 1 << n;
        vector<vector<int>> subs(p);
        for (int i = 0; i < p; i++) {
            for (int j = 0; j < n; j++) {
                // 用 i>>j & 1的方式遍历每一位
                if ((i >> j) & 1) {
                    subs[i].push_back(nums[j]);
                }
            }
        }
        return subs;
    }
```

**5、 位图**

**描述：有一千万个整数，整数范围在1到1亿之间， 如何快速查找某个整数是否在这1千万个整数中。**

**思路： 用一个bit 数组来存储这1-1亿之间的数。如果数字存在， 在对应的下标上标1， 1亿个数只需要1亿个bit位。**

```java
public class BitMap { // Java 中 char 类型占 16bit，也即是 2 个字节
  private char[] bytes;
  private int nbits;
  
  public BitMap(int nbits) {
    this.nbits = nbits;
    this.bytes = new char[nbits/16+1];
  }

  public void set(int k) {
    if (k > nbits) return;
    int byteIndex = k / 16;
    int bitIndex = k % 16;
    bytes[byteIndex] |= (1 << bitIndex);
  }

  public boolean get(int k) {
    if (k > nbits) return false;
    int byteIndex = k / 16;
    int bitIndex = k % 16;
    return (bytes[byteIndex] & (1 << bitIndex)) != 0;
  }
}
```

## 190 颠倒的二进制位

颠倒给定的 32 位无符号整数的二进制位。

```
示例1：

输入: 00000010100101000001111010011100
输出: 00111001011110000010100101000000
解释: 输入的二进制串 00000010100101000001111010011100 表示无符号整数 43261596，
因此返回 964176192，其二进制表示形式为 00111001011110000010100101000000。
```

```java
public int reverseBits(int n) {
        int t = 0;
        for(int i = 0;i<32;i++) 
            t+= (1&(n>>i))<<(31-i);
        return t;
    }
```

## 位1的个数

```
编写一个函数，输入是一个无符号整数，返回其二进制表达式中数字位数为 ‘1’ 的个数。
示例1：
输入：00000000000000000000000000001011
输出：3
解释：输入的二进制串 00000000000000000000000000001011 中，共有三位为 '1'。
```

### 思路一：位运算

利用循环右移操作，每次移动1位，并且取出末尾与1做&操作，若不为1，说明末尾是0。

```java
public int hammingWeight(int n) {
         int cnt = 0;
        for(int i=0;i<32;i++)
        {
            cnt += n&1;
            n >>=1;
        }
        return cnt;
    }
```

### 思路二：n与n-1做位运算

当n&(n-1)运算，会把最后一个1的位变成0。

```java
public int hammingWeight(int n) {
        int cnt = 0;
        while (n != 0) {
           ++cnt;
           n = n & (n - 1);
        }
        return cnt;
    }
```

## 231 2的幂

```
给定一个整数，编写一个函数来判断它是否是 2 的幂次方。
示例1：

输入: 1
输出: true
解释: 2^0 = 1
```

二分查找采用打表和二分查找的方法，将int范围内的所有2^n全部存入一个整数表中，然后对整数表进行二分查找。

```java
public boolean isPowerOfTwo(int n) {
    if (n <= 0) return false;
    return (n & (n - 1)) == 0? true : false;
}
```

## 两整数之和

```
不使用运算符 + 和 - ，计算两整数a、b之和。
示例1：

输入: a = 1, b = 2
输出: 3
不用运算符，考虑位运算。a^b 得到不考虑进位的a+b结果；a&b<<1得到a+b的进位。
```

```java
public int getSum(int a, int b) {
        while(b!=0) {
            int carry = (a&b)<<1;
            a = a^b;
            b = carry;
        }
        return a;
    }
```

## 405 数字转化为十六进制

```
给定一个整数，编写一个算法将这个数转换为十六进制数。对于负整数，我们通常使用补码运算。

**示例1**：

> 输入:
>  26

输出:
 "1a"

**示例2**：

> 输入:
>  -1

输出:
 "ffffffff"

**注意**：

> 十六进制中所有字母(a-f)都必须是小写。
>  十六进制字符串中不能包含多余的前导零。如果要转化的数为0，那么以单个字符'0'来表示；对于其他情况，十六进制字符串中的第一个字符将不会是0字符。
>  给定的数确保在32位有符号整数范围内。
>  不能使用任何由库提供的将数字直接转换或格式化为十六进制的方法。

**示例1**：

> 输入:
>  26

输出:
 "1a"

**示例2**：

> 输入:
>  -1

输出:
 "ffffffff"
```
位运算
```java
public String toHex(int num) {
        if(num==0) return "0";
        char[] dict = {'0','1','2','3','4','5','6','7','8','9',
            'a','b','c','d','e','f'};
        StringBuffer sb = new StringBuffer();
        while(num!=0) {
            sb.append(dict[num&0xf]);
            num = num >>> 4;
        }
        return sb.reverse().toString();
    }
```




