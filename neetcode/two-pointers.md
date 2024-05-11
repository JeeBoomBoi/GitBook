# Two Pointers

## 125. Valid Palindrome
link - [https://leetcode.com/problems/valid-palindrome/description/](https://leetcode.com/problems/valid-palindrome/description/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public boolean isPalindrome(String s) {
        int i = 0;
        int j = s.length() - 1;
        while (i < j) {
            char a = s.charAt(i);
            char b = s.charAt(j);
            if (!Character.isLetterOrDigit(a)) {
                i++;
                continue;
            }

            if (!Character.isLetterOrDigit(b)) {
                j--;
                continue;
            }

            if (Character.toLowerCase(a) != Character.toLowerCase(b)) {
                return false;
            }

            i++;
            j--;
        }
        return true;
    }
}
```
{% endtab %}
{% endtabs %}

## 167. Two Sum II - Input Array Is Sorted
link - [https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int i = 0;
        int length = numbers.length;
        int j = length - 1;
        while (i < length - 1 && j > i) {
            if (numbers[i] + numbers[j] == target) {
                return new int[]{i + 1, j + 1};
            } 
            if (numbers[i] + numbers[j] < target) {
                i++;
            } else {
                j--;
            }     
        }
        return new int[]{};
    }
}
```
{% endtab %}
{% endtabs %}
