# Day 8

**1. Sieve of Eratosthenes**

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
```
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

**2.Computing Power**

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
```
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

**3.Iterative Power\(Fast Exponentiation\)**

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
Space Complexity: O\(1\)

