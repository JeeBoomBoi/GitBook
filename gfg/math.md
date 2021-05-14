**1. LCM and GCD of two numbers**

{% tabs %}
{% tab title="CPP" %}
```text
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
```text
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

Time complexity : O\(log\(min\(a,b\)\)\) Space complexity: O\(1\)

**2. Check for Prime**

{% tabs %}
{% tab title="CPP" %}
```text
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
```text
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

Time Complexity : O\(sqrt\(N\)\) Space Complexity: O\(1\)

**3. Highest Prime Factor**

{% tabs %}
{% tab title="CPP" %}
```text
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
```text
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

Time Complexity : O\(sqrt\(N\)\) Space Complexity: O\(1\)

**4. All divisors of a number**

{% tabs %}
{% tab title="CPP" %}
```text
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
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(sqrt\(N\)\) Space Complexity: O\(1\)

**5. Sieve of Eratosthenes**

{% tabs %}
{% tab title="CPP" %}
```text
public:
    vector<int> sieveOfEratosthenes(int n)
    {
        // Write Your Code here
        bool prime[n + 1];
        memset(prime, true, sizeof(prime));

        vector<int> res;
        for (int i = 2; i * i <= n; i++)
        {
            if (prime[i] == true)
            {
                for (int j = i * i; j <= n; j = j + i)
                {
                    prime[j] = false;
                }
            }
        }
        for (int i = 2; i <= n; i++)
        {
            if (prime[i] == true)
            {
                res.push_back(i);
            }
        }
        return res;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text
def sieveOfEratosthenes(self, n):
        #code here 
        prime = [True for i in range(n+1)]
        res = []
        p = 2

        while p * p <= n:
            if prime[p] == True:
                for i in range(p * p, n+1, p):
                    prime[i] = False

            p += 1

        for i in range(2, n+1):
            if prime[i] == True:
                res.append(i)

        return res
```
{% endtab %}
{% endtabs %}

Time Complexity : O\(loglog\(n\)\)  
Space Complexity: O\(n\)

**6.Computing Power**

{% tabs %}
{% tab title="CPP" %}
```text
public:
    //You need to complete this fucntion

    long long power(int n,int p)
    {
       //Your code here
       if (p == 0)  
            return 1;
        long long temp = power(n, p / 2);
        temp = (temp * temp) % 1000000007;
        if (p % 2 == 0)
        {
            return temp % 1000000007;
        }
        else 
        {
            return (temp * n) % 1000000007;
        }
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text
class Solution:
    #Complete this function
    def power(self,n,r):
        #Your code here
        temp = 0
        if (r == 0):
            return 1
        temp = self.power(n, int(r/2))
        if (r % 2 == 0):
            return temp * temp % 1000000007
        else:
            return n * temp * temp % 1000000007
```
{% endtab %}
{% endtabs %}

Time Complexity : O\(log\(n\)\)  
Space Complexity: O\(log\(n\)\)

**7.Iterative Power\(Fast Exponentiation\)**

{% tabs %}
{% tab title="CPP" %}
```text
public:
    long long int power(long long int a, long long int b) { 
        //complete the function here
        long long res = 1;
        while(b > 0)
        {
            if (b & 1)
            {
                res = (res * a) % 1000000007;
            }
            a = (a * a) % 1000000007;
            b = b >> 1;
        }
        return res % 1000000007;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(log\(n\)\)  
Space Complexity: O\(1)
