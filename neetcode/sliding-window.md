# Sliding Window

## 121. Best Time to Buy and Sell Stock
link - [https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int maxProfit(int[] prices) {
        int l = 0;
        int r = l + 1;
        int maxProfit = 0;

        while (r != prices.length) {
            if (prices[l] >= prices[r]) {
                l = r;
            }
            else {
                maxProfit = Math.max(maxProfit, prices[r] - prices[l]);
            }
            r++;
        }
        return maxProfit;
    }
}
```
{% endtab %}
{% endtabs %}
