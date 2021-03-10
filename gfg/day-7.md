# Day-6

**1. All divisors of a number**
{% tabs %}
{% tab title="CPP" %}
```
 public:
    int kThSmallestFactor(int n , int k) {
        // code here
        
        int divisorCount = 0;
        for (int i = 1; i * i < n; i++) 
        {
            if (n % i == 0)
                divisorCount++;
            if (divisorCount == k)
                return i;
        }
        for (int i = sqrt(n); i >= 1; i--)
        {
            if (n % i == 0)
                divisorCount++;
            if (divisorCount == k)
                return n / i;
        }
        return -1;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(sqrt(N))
Space Complexity: O(1)