# Arrays & Hashing

## 217. Contains Duplicate
link - [https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)

{% tabs %}
{% tab title="Python" %}
```text
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        my_set = set()
        for i in nums:
            if i in my_set:
                return True
            my_set.add(i)
        return False
```
{% endtab %}