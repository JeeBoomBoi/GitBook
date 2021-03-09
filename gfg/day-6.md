# Day 6

**1. GCD and LCM of two numbers**

{% tab title="CPP" %}
```
public:
    long long gcd(long long a, long long b) {
        if (b == 0)
            return a;
        return gcd(b, a % b);
    }
    
    long long lcm(long long a, long long b) {
        return (a * b) / gcd(a, b);
    }
    vector<long long> lcmAndGcd(long long A , long long B) {
        // code here
        vector<long long> res;
        res.push_back(lcm(A, B));
        res.push_back(gcd(A, B));
        return res;
    }
``` 
{% endtab %}
