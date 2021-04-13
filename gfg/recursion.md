# Recursion

**1. Print 1 To N Without Loop**  
Problem link: [link](https:/t.ly/DFSF)
{% tabs %}
{% tab title="CPP" %}
```
class Solution{
    public:
    //Complete this function
    void printNos(int n)
    {
        //Your code here
        if (n == 0)
            return;
        printNos(n - 1);
        cout << n << " ";
    }
};
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(N)   
Space Complexity: O(N)


**2. Sum of Digits of a Number**  
Problem link: [link](https://t.ly/wfJF)
{% tabs %}
{% tab title="CPP" %}
```
class Solution{
  public:
    // Complete this function
    int sumOfDigits(int n)
    {
        //Your code here
        if (n == 0)
            return 0;
        int k = n % 10;
        return k + sumOfDigits(n / 10);
    }
};
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(Logn)   
Space Complexity: O(Logn)


**3. Count Total Digits in a Number**  
Problem link: [link](https://t.ly/L5AB)
{% tabs %}
{% tab title="CPP" %}
```
class Solution{
  public:
    //Complete this function
    int countDigits(int n)
    {
       //Your code here
       if (n < 10)
            return 1;
       return 1 + countDigits(n / 10);
    }
};
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(logn)   
Space Complexity: O(logn)

**4. Digital Root**  
Problem link: [link](https://t.ly/6gTY)
{% tabs %}
{% tab title="CPP" %}
```
class Solution{
  public:
    //Complete this function
    int digitalRoot(int n)
    {
        //Your code here
        if (n < 10)
            return n;
        return digitalRoot(n % 10 + n / 10);
    }
};
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O((Num of Digits)^2)   
Space Complexity: O(Num of Digits)


**5. Fibonacci Using Recursion**  
Problem link: [link](https://t.ly/MuBW)
{% tabs %}
{% tab title="CPP" %}
```
class Solution{
    public:
    //Complete this function
    int fibonacci(int n)
    {
        //Your code here
        if (n <= 1)
            return n;
        return fibonacci(n-1) + fibonacci(n-2);
    }
};
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(2^n)   
Space Complexity: O(n)

**6. Tower Of Hanoi**  
Problem link: [link](https://)
{% tabs %}
{% tab title="CPP" %}
```
class Solution{
    public:
    // You need to complete this function

    // avoid space at the starting of the string in "move disk....."
    long long toh(int n, int a, int b, int c) {
    //Your code here
    // ToH(N, from, to, aux);
    if (n == 1)
    {
        cout << "move disk 1 from rod " << a << " to rod " << b << endl;
        return 1;
    }
    toh(n - 1, a, c, b);
    cout << "move disk " << n << " from rod " << a << " to rod " << b << endl;
    toh(n - 1, c, b, a);
    return pow(2,n)-1;
}

};
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(2^n)   
Space Complexity: O(n)


**7. Josephus problem**  
Problem link: [link](https://t.ly/84F2)
{% tabs %}
{% tab title="CPP" %}
```
class Solution
{
    public:
    int jos(int n, int k)
    {
        if (n == 1)
            return 0;
        else
            return ((jos(n-1, k) + k) % n);
    }
    int josephus(int n, int k)
    {
       //Your code here
       return jos(n, k) + 1;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(n)   
Space Complexity: O(n)


**8. Power Using Recursion**  
Problem link: [link](https://t.ly/rgW8)
{% tabs %}
{% tab title="CPP" %}
```
int RecursivePower(int n, int p)
{
    //Your code here
    // long long int mod = pow(10, 9) + 7;
    return p == 0 ? 1 : (n * RecursivePower(n, p - 1));
} 
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(p)   
Space Complexity: O(p)


**9. Power Of Numbers**  
Problem link: [link](https://t.ly/cP2R)
{% tabs %}
{% tab title="CPP" %}
```
class Solution{
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

```
{% endtab %}
{% endtabs %}

Time Complexity : O(logn)   
Space Complexity: O(logn)


**10. Power Set Using Recursion**  
Problem link: [link](https://)
{% tabs %}
{% tab title="CPP" %}
```
void getAllSet(string s, int i, string curr, vector<string> &v)
{
    if(i == s.length())
    {
        v.push_back(curr);
        return;
    }
    getAllSet(s, i + 1, curr, v);
    getAllSet(s, i + 1, curr + s[i], v);
}

vector <string> powerSet(string s)
{
   //Your code here
    vector<string> v;
    getAllSet(s, 0, "", v);
    return v;
}
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(2^|s|)   
Space Complexity: O(|s|)