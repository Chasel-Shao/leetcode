## Basic Claculator Iv

----
## 题目地址

[https://leetcode.com/problems/basic-calculator-iv/](https://leetcode.com/problems/basic-calculator-iv/)

## 题目描述

```text
Given an expression such as expression = "e + 8 - a + 5" and an evaluation map such as {"e": 1} (given in terms of evalvars = ["e"] and evalints = [1]), return a list of tokens representing the simplified expression, such as ["-1*a","14"]

An expression alternates chunks and symbols, with a space separating each chunk and symbol.
A chunk is either an expression in parentheses, a variable, or a non-negative integer.
A variable is a string of lowercase letters (not including digits.) Note that variables can be multiple letters, and note that variables never have a leading coefficient or unary operator like "2x" or "-x".
Expressions are evaluated in the usual order: brackets first, then multiplication, then addition and subtraction. For example, expression = "1 + 2 * 3" has an answer of ["7"].

The format of the output is as follows:

For each term of free variables with non-zero coefficient, we write the free variables within a term in sorted order lexicographically. For example, we would never write a term like "b*a*c", only "a*b*c".
Terms have degree equal to the number of free variables being multiplied, counting multiplicity. (For example, "a*a*b*c" has degree 4.) We write the largest degree terms of our answer first, breaking ties by lexicographic order ignoring the leading coefficient of the term.
The leading coefficient of the term is placed directly to the left with an asterisk separating it from the variables (if they exist.)  A leading coefficient of 1 is still printed.
An example of a well formatted answer is ["-2*a*a*a", "3*a*a*b", "3*b*b", "4*a", "5*c", "-6"] 
Terms (including constant terms) with coefficient 0 are not included.  For example, an expression of "0" has an output of [].
Examples:

Input: expression = "e + 8 - a + 5", evalvars = ["e"], evalints = [1]
Output: ["-1*a","14"]

Input: expression = "e - 8 + temperature - pressure",
evalvars = ["e", "temperature"], evalints = [1, 12]
Output: ["-1*pressure","5"]

Input: expression = "(e + 8) * (e - 8)", evalvars = [], evalints = []
Output: ["1*e*e","-64"]

Input: expression = "7 - 7", evalvars = [], evalints = []
Output: []

Input: expression = "a * b * c + b * a * c * 4", evalvars = [], evalints = []
Output: ["5*a*b*c"]

Input: expression = "((a - b) * (b - c) + (c - a)) * ((a - b) + (b - c) * (c - a))",
evalvars = [], evalints = []
Output: ["-1*a*a*b*b","2*a*a*b*c","-1*a*a*c*c","1*a*b*b*b","-1*a*b*b*c","-1*a*b*c*c","1*a*c*c*c","-1*b*b*b*c","2*b*b*c*c","-1*b*c*c*c","2*a*a*b","-2*a*a*c","-2*a*b*b","2*a*c*c","1*b*b*b","-1*b*b*c","1*b*c*c","-1*c*c*c","-1*a*a","1*a*b","1*a*c","-1*b*c"]
Note:

expression will have length in range [1, 250].
evalvars, evalints will have equal lengths in range [0, 100].
```

## 代码

Approach 1:

```java
class Solution {
public List<String> basicCalculatorIV(String expression, String[] evalvars, int[] evalints) {
  Map<String, Integer> evalMap = new HashMap();
  for (int i = 0; i < evalVars.length; i++) {
    evalMap.put(evalVars[i], evalInts[i]);
  }
    return parse(expression).evaluate(evalMap).toList();
  }

  public Poly make(String expr) {
    Poly ans = new Poly();
    List<String> list = new ArrayList();
    if (Character.isDigit(expr.charAt(0))) {
      // digit : { [] => count }
      ans.update(list, Integer.valueOf(expr));
    } else {
        // letter : { [letter] => count}
      list.add(expr);
      ans.update(list, 1);
    }
    return ans;
  }

  public Poly combine(Poly left, Poly right, char symbol) {
    if (symbol == '+') return left.add(right);
        if (symbol == '-') return left.sub(right);
        if (symbol == '*') return left.mul(right);
    throw null;
  }

  public Poly parse(String expr) {
    List<Poly> bucket = new ArrayList();
    List<Character> symbols = new ArrayList();
    int i = 0;
    while (i < expr.length()) {
      // 1. tackle the '()'
      if (expr.charAt(i) == '(') {
        int bal = 0, j = i;
        for (; j < expr.length(); j++) {
          if (expr.charAt(j) == '(') bal++;
          if (expr.charAt(j) == ')') bal--;
          if (bal == 0) break;
        }
        bucket.add(parse(expr.substring(i + 1, j)));
        i = j;
      } else if (Character.isLetterOrDigit(expr.charAt(i))) {
        // 2. tackle each element
        int j = i;
          for (; j < expr.length(); j++) {
            if (expr.charAt(j) == ' ') {
              break;
            }
          }
        bucket.add(make(expr.substring(i, j)));
        i = j;
      } else if (expr.charAt(i) != ' ') {
        // 3. tackle symbols, + - *
        symbols.add(expr.charAt(i));
      }

      i++;
    }

    for (int j = symbols.size() - 1; j >= 0; j--) {
      if (symbols.get(j) == '*') {
        bucket.set(j, combine(bucket.get(j), bucket.remove(j + 1)，symbols.remove(j)));
      }
    }

    if (bucket.isEmpty()) return new Poly();
    Poly ans = bucket.get(0);
    for (int j = 0; j < symbols.size(); j++) {
      ans = combine(ans, bucket.get(j + 1), symbols.get(j));
    }

    return ans;
  }
}

class Poly {
  HashMap<List<String>, Integer> count;
  Poly() {
    count = new HashMap();
  }

  void update(List<String> key, int val) {
    this.count.put(key, this.count.getOrDefault(key, 0) + val);
  }

  Poly add(Poly that) {
    Poly ans = new Poly();
    for (List<String> k : this.count.keySet()) {
      ans.update(k, this,count.get(k));
    }
    for (List<String> k : that.count.keySet()) {
      ans.update(k, that.count.get(k));
    }
    return ans;
  }

  Poly sub(Poly that) {
    Poly ans = new Poly();
    for (List<String> k : this.count.keySet()) {
      ans.update(k, this.count.get(k));
    }
    for (List<String> k : that.count.keySet()) {
      ans.update(k, -that.count.get(k));
    }
    return ans;
  }

  Poly mul(Poly that) {
    Poly ans = new Poly();
    for (List<String> k1 : this.count.keySet()) {
      for (List<String> k2 : that.count.keySet()) {
        List<String> kNew = new ArrayList();
        for (String x : k1) kNew.add(x);
        for (String x : k2) kNew.add(x);
        Collections.sort(kNew);
        ans.update(kNew, this.count.get(k1) * that.count.get(k2));
      }
    }

    return ans;
  }

  Poly evaluate(Map<String, Integer> evalMap) {
    Poly ans = new Poly();
    for (List<String> k : this.count.keySet()) {
      int c = this.count.get(k);
      List<String> free = new ArrayList();
      for (String token : k) {
        if (evalMap.containsKey(token)) {
          c *= evalMap.get(token);
        } else {
          free.add(token);
        }
      }
      ans.update(free, c);
    }

    return ans;
  }

  int compareList(List<String> A, List<String> B) {
    int i = 0;
    for (String x : A) {
      String y = B.get(i++);
      if (x.compareTo(y) != 0) {
        return x.compareTo(y);
      }
    }
    return 0;
  }

  List<String> toList() {
    List<String> ans = new ArrayList();
    List<List<String>> keys = new ArrayList(this.count.keySet());
    Collections.sort(keys, (a, b) -> 
                     a.size() != b.size() ? b.size() - a.size() : compareList(a, b));

    for (List<String> key : keys) {
      int v = this.count.get(key);
      if (v == 0) continue;
      StringBuilder word = new StringBuilder();
      word.append("" + v);
      for (String token : key) {
        word.append('*');
        word.append(token);
      }
      ans.add(word.toString());
    }

    return ans;
  }
}
```

