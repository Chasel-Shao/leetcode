## Restore Ip Address

----
## 题目地址

https://leetcode.com/problems/restore-ip-addresses/

## 题目描述
```
Given a string containing only digits, restore it by returning all possible valid IP address combinations.

Example:

Input: "25525511135"
Output: ["255.255.11.135", "255.255.111.35"]
```

## 代码

Approach 1: Backtracking (DFS)

```java
class Solution {
  public List<String> restoreIpAddresses(String s) {
    List<String> result = new ArrayList<>();
    dfs(result, "", s, 0);
    return result;
  }
  
  private void dfs(List<String> result, String ip, String substring, int level) {
    if (substring.isEmpty() || level == 4) {
      if (s.isEmpty() && level == 4) {
        result.add(ip);
      }
      return;
    }
    int len = substring.charAt(0) == '0' ? 1 : 3;
    len = Math.min(len, substring.length());
    for (int i = 1; i <= len; i++) {
      String part = substring.substring(0, i);
      if (Integer.valueOf(part) <= 255) {
        if (ip.length() > 0) ip += ".";
        ip += part;
        dfs(result, ip, substring.substring(i), level + 1);
      }
    }
  }
  
}
```

DFS #2

```java
class Solution {
  public List<String> restoreIpAddresses(String s) {
    List<String> ans = new ArrayList<String>();
    LinkedList<String> segments = new LinkedList<String>();
    
    backtrack(ans, segments, s, 0);
    return ans;
  }

  public void backtrack(List<String> ans, LinkedList<String> segments, String s, int start_pos) {
    int max_pos = Math.min(s.length() - 1, start_pos + 3);
    for (int curr_pos = start_pos; curr_pos < max_pos; curr_pos++) {
      String segment = s.substring(start_pos, curr_pos + 1);
      if (valid(segment)) {
        segments.add(segment);
        if (segments.size() == 3) {
            String next_segment = s.substring(curr_pos + 1, s.length());
            if (valid(next_segment)) {
              segments.add(next_segment);
              ans.add(String.join(".", segments));
              segments.removeLast();
            }
        } else {
          backtrack(ans, segments, s, curr_pos + 1);
        }
        segments.removeLast();
      }
    }
  }
  
  public boolean valid(String part) {
    int len = part.length();
    if (len > 3)	return false;
    if (part.charAt(0) == '0') {
      return len == 1;
    } else {
      return Integer.valueOf(part) <= 255;
    } 
  }

}
```

Approach #2

```java
public List<String> restoreIpAddresses(String s) {
		List<String> ret = new ArrayList<>();
		
		StringBuffer ip = new StringBuffer();
		for(int a = 1 ; a < 4 ; ++ a)
		for(int b = 1 ; b < 4 ; ++ b)
	  for(int c = 1 ; c < 4 ; ++ c)
		for(int d = 1 ; d < 4 ; ++ d)
		{
			if(a + b + c + d == s.length() )
			{
				int n1 = Integer.parseInt(s.substring(0, a));
				int n2 = Integer.parseInt(s.substring(a, a+b));
				int n3 = Integer.parseInt(s.substring(a+b, a+b+c));
				int n4 = Integer.parseInt(s.substring(a+b+c));
				if(n1 <= 255 && n2 <= 255 && n3 <= 255 && n4 <= 255)
				{
					ip.append(n1).append('.').append(n2)
						.append('.').append(n3).append('.').append(n4);
					if(ip.length() == s.length() + 3) ret.add(ip.toString());
					ip.delete(0, ip.length());
				}
			}
		}
		return ret;
    }
}
```











