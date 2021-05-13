# Day1

1/2/2021

Revising Team Blind 75

1\) Two Sum - [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

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

{% tab title="CPP" %}
```text
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> hm;
        vector<int> result;

        for (int i = 0; i < nums.size(); i++)
        {
            int rem = target - nums[i];

            if (hm.find(rem) != hm.end())
            {
                result.push_back(hm[rem]);
                result.push_back(i);
                return result;
            }

            hm[nums[i]] = i;
        }

        return result;
    }
};
```
{% endtab %}
{% endtabs %}

2\) Best time to buy and sell stock - [https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

{% tabs %}
{% tab title="Python" %}
```text
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if (len(prices) <= 1):
            return 0

        max_profit = 0
        curr = prices[0]

        for i in range(1, len(prices)):
            max_profit = max(max_profit, prices[i] - curr)

            if prices[i] < curr:
                curr = prices[i]

        return max_profit
```
{% endtab %}

{% tab title="CPP" %}
```text
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if (prices.size() <= 1) 
            return 0;

        int maxProfit = 0;
        int curr = prices[0];

        for (int i = 1; i < prices.size(); i++) {
            if (prices[i] > prices[i-1]) {
                maxProfit = max(maxProfit, prices[i] - curr);
            } else {
                curr = min(curr, prices[i]);
            }
        }

        return maxProfit;
    }
};
```
{% endtab %}
{% endtabs %}

3\) Contains Duplicate - [https://leetcode.com/problems/contains-duplicate](https://leetcode.com/problems/contains-duplicate)

{% tabs %}
{% tab title="Python" %}
```text
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        dic = {}
        for i in nums:
            if i in dic:
                return True
            else:
                dic[i] = True

        return False
```
{% endtab %}

{% tab title="CPP" %}
```text
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_map<int, int> hm;
        for (int i = 0; i < nums.size(); i++) {
            if (hm.find(nums[i]) != hm.end()) {
                return true;
            }
            hm[nums[i]] = 1;
        }
        return false;
    }
};
```
{% endtab %}
{% endtabs %}

4\) Product of Array Except Self - [https://leetcode.com/problems/product-of-array-except-self/](https://leetcode.com/problems/product-of-array-except-self/)

{% tabs %}
{% tab title="Python" %}
```text
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        p = 1
        result = []
        for i in range(0, len(nums)):
            result.append(p)
            p = p * nums[i]

        p = 1
        for i in range(len(nums) - 1, -1, -1):
            result[i] = result[i] * p
            p = p * nums[i]

        return result
```
{% endtab %}

{% tab title="CPP" %}
```text
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int p = 1;
        vector<int> result;
        for(int i = 0; i < nums.size(); i++) {
            result.push_back(p);
            p = p * nums[i];
        }

        p = 1;

        for(int i = nums.size() - 1; i >= 0; i--) {
            result[i] = result[i] * p;
            p = p * nums[i];
        }

        return result;
    }
};
```
{% endtab %}
{% endtabs %}

