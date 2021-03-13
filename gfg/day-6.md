# Day-6

**1. LCM and GCD of two numbers**

{% tabs %}
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

{% tab title="Python" %}
```
class Solution:
    
    def gcd(self, a, b):
        if b == 0:
            return a;
        return self.gcd(b, a % b)
    
        
    def lcm(self, a, b):
        return (a * b) / self.gcd(a, b);
        
    
    def lcmAndGcd(self, a , b):
        # code here 
        li = []
        t1 = self.gcd(a, b)
        t2 = int(self.lcm(a, b))
        li.append(t2)
        li.append(t1)
        return li
```
{% endtab %}
{% endtabs %}

Time complexity : O(log(min(a,b)))
Space complexity: O(1)


**2. Check for Prime**
{% tabs %}
{% tab title="CPP" %}
```
public:
    int isPrime(int n){
        // code here
        if (n == 1)
            return 0;
        if (n == 2 || n == 3)
            return 1;
        if (n % 2 == 0 || n % 3 == 0)
            return 0;
        for (int i = 5; i * i <= n; i += 6)
        {
            if (n % i == 0 || n % (i + 2) == 0)
                return 0;
        }
        return 1;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```
import math
class Solution:
    def isPrime (self, n):
        # code here
        if n == 1:
            return 0
        if n == 2 or n == 3:
            return 1
        if n % 2 == 0 or n % 3 == 0:
            return 0
        for i in range(5, int(math.sqrt(n))+1, 6):
            if n % i == 0 or n % (i + 2) == 0:
                return 0
        return 1
```
{% endtab %}
{% endtabs %}

Time Complexity : O(sqrt(N))
Space Complexity: O(1)


**3. Highest Prime Factor**
{% tabs %}
{% tab title="CPP" %}
```
public: 
    long long int largestPrimeFactor(int n){
        // code here
        long long max = 0;
        for (int i = 2; i * i <= n; i++)
        {
            while(n % i == 0)
            {
                max = i;
                n = n / i;
            }
        }
        if (n > 1)
        {
            max = n;
        }
        return max;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```
import math
class Solution:
    def largestPrimeFactor (self, n):
        # code here
        max = 0
        for i in range(2, int(math.sqrt(n) + 1), 1):
            while n % i == 0:
                max = i
                n = n / i
                
        if n > 1:
            max = n
        return int(max)
```
{% endtab %}
{% endtabs %}

Time Complexity : O(sqrt(N))
Space Complexity: O(1)
