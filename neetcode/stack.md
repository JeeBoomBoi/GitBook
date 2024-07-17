# Stack

## 20. Valid Parentheses
link - [https://leetcode.com/problems/valid-parentheses/description/](https://leetcode.com/problems/valid-parentheses/description/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public boolean isValid(String s) {
        int n = s.length();
        if (n % 2 != 0) return false;
        Stack<Character> stack = new Stack();
        HashMap<Character, Character> hashMap = new HashMap<>();

        hashMap.put(')', '(');
        hashMap.put(']', '[');
        hashMap.put('}', '{');

        for (int i = 0; i < n; i++) {
            char c = s.charAt(i);
            if (c == '(' || c == '[' || c == '{') {
                stack.push(c);
            } else {
                if (stack.empty()) return false;
                char top = stack.pop();
                if (top != hashMap.get(c)) return false;
            }
        }
        if (!stack.empty()) return false;
        return true;
    }
}
```
{% endtab %}
{% endtabs %}

## 155. Min Stack
link - [https://leetcode.com/problems/min-stack/description/](https://leetcode.com/problems/min-stack/description/)

{% tabs %}
{% tab title="Java" %}
```java
class MinStack {

    private Stack<Integer> stack;
    private Stack<Integer> minStack;

    public MinStack() {
        stack = new Stack();
        minStack = new Stack();
    }
    
    public void push(int val) {
        stack.push(val);
        if (minStack.empty()) {
            minStack.push(val);
        } else {
            minStack.push(val < minStack.peek() ? val : minStack.peek());
        }
    }
    
    public void pop() {
        stack.pop();
        minStack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
        return minStack.peek();
    }
}
```
{% endtab %}
{% endtabs %}

## 150. Evaluate Reverse Polish Notation
link - [https://leetcode.com/problems/evaluate-reverse-polish-notation/description/](https://leetcode.com/problems/evaluate-reverse-polish-notation/description/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack();
        for (String t : tokens) {
            if (t.equals("+")) {
                int a = stack.pop();
                int b = stack.pop();
                stack.push(a + b);
            } else if (t.equals("-")) {
                int b = stack.pop();
                int a = stack.pop();
                stack.push(a - b);
            } else if (t.equals("/")) {
                int b = stack.pop();
                int a = stack.pop();
                stack.push(a / b);
            } else if (t.equals("*")) {
                int a = stack.pop();
                int b = stack.pop();
                stack.push(a * b);
            } else {
                int num = Integer.parseInt(t);
                stack.push(num);
            }
        }
        return stack.pop();
    }
}
```
{% endtab %}
{% endtabs %}

## 22. Generate Parentheses
link - [https://leetcode.com/problems/generate-parentheses/description/](https://leetcode.com/problems/generate-parentheses/description/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    List<String> res = new ArrayList();
    Stack<Character> stack = new Stack();
    public List<String> generateParenthesis(int n) {
        backtrack(0, 0, n);
        return res;
    }

    public void backtrack(int open, int close, int n) {

        if (open == n && close == n) {
            Iterator it = stack.iterator();
            String temp = "";
            while(it.hasNext()) {
                temp = temp + it.next();
            }
            res.add(temp);
        }

        if (open < n) {
            stack.push('(');
            backtrack(open + 1, close, n);
            stack.pop();
        }

        if (close < open) {
            stack.push(')');
            backtrack(open, close + 1, n);
            stack.pop();
        }
    }
}
```
{% endtab %}
{% endtabs %}

## 739. Daily Temperatures
link - [https://leetcode.com/problems/daily-temperatures/description/](https://leetcode.com/problems/daily-temperatures/description/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {

    public int[] dailyTemperatures(int[] temperatures) {
        int[] ans = new int[temperatures.length];
        Stack<Integer> stack = new Stack<>();
        for (int currDay = 0; currDay < temperatures.length; currDay++) {
            while (
                !stack.isEmpty() &&
                temperatures[currDay] > temperatures[stack.peek()]
            ) {
                int prevDay = stack.pop();
                ans[prevDay] = currDay - prevDay;
            }
            stack.add(currDay);
        }
        return ans;
    }
}

```
{% endtab %}
{% endtabs %}

## 853. Car Fleet
link - [https://leetcode.com/problems/car-fleet/](https://leetcode.com/problems/car-fleet/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int carFleet(int target, int[] position, int[] speed) {
        Stack<Double> stack = new Stack();
        int[][] combine = new int[position.length][2];
        for (int i = 0; i < position.length; i++) {
            combine[i][0] = position[i];
            combine[i][1] = speed[i];
        }

        Arrays.sort(combine, java.util.Comparator.comparingInt(i -> i[0]));
        for (int j = combine.length - 1; j >= 0; j--) {
            double time = (double) (target - combine[j][0]) / combine[j][1];
            if (!stack.empty() && time <= stack.peek()) {
                continue;
            } else {
                stack.push(time);
            }
        }

        return stack.size();
    }
}
```
{% endtab %}
{% endtabs %}

## 84. Largest Rectangle in Histogram
link - []()

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int largestRectangleArea(int[] heights) {
        Stack<Pair<Integer, Integer>> stack = new Stack<>();
        int n = heights.length;
        int area = 0;
        int start;
        for (int i = 0; i < n; i++) {
            int currHeight = heights[i];
            start = i;
            while (!stack.isEmpty() && stack.peek().getValue() > currHeight) {
                Pair<Integer, Integer> pair = stack.pop();
                int index = pair.getKey();
                int ht = pair.getValue();
                area = Math.max(area, ht * (i - index));
                start = index;
            }
            stack.push(new Pair(start, currHeight));
        }

        while(!stack.isEmpty()) {
            Pair<Integer, Integer> pair = stack.pop();
            int index = pair.getKey();
            int ht = pair.getValue();
            area = Math.max(area, ht * (n - index));
        }

        return area;
    }
}
```
{% endtab %}
{% endtabs %}
