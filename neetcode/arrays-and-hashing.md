# Arrays & Hashing

## 217. Contains Duplicate
link - [https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)

{% tabs %}
{% tab title="Python" %}
```text
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dictionary = {}

        for i, value in enumerate(nums):
            rem = target - value

            if rem in dictionary:
                return [dictionary[rem], i]
            else:
                dictionary[value] = i
```
{% endtab %}