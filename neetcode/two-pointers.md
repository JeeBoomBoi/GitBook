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
