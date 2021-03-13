# Day 9

**1. Find first set bit**  
Problem link: [link](t.ly/1K0c)
{% tabs %}
{% tab title="CPP" %}
```
public:
    /*  function to find position of first set 
    bit in the given number
     * n: given input for which we want to get
          the position of first set bit
     */
    unsigned int getFirstSetBit(int n){
        
        // Your code here
        if (n == 0)
            return 0;
        unsigned int num = 1;
        int k = 0;
        while(true)
        {
            if ((n >> k) & 1)
                return num;
            else
            {
                k++;
                num++;
            }
        }
        return 0;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(log(n))  
Space Complexity: O(n)

**2. Rightmost different bit**  
Problem link: [link](t.ly/w7ii)
{% tabs %}
{% tab title="CPP" %}
```
public:
    /*  Function to find the first position with different bits
    *   This function returns the position with different bit
    */
    int posOfRightMostDiffBit(int m, int n)
    {
        
        // Your code here
        int k = 0;
        while(((m >> k) & 1) == ((n >> k) & 1))
        {
            k++;
        }
        return k + 1;
        
    }
};
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(max(log m, log n))   
Space Complexity: O(1)

**3. Check whether K-th bit is set or not**  
Problem link: [link](t.ly/4qFH)
{% tabs %}
{% tab title="CPP" %}
```
public:
    bool checkKthBit(int n, int k){
    
    // Your code here
    // It can be a one liner logic!! Think of it!!
    return (n >> k) & 1;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O(log n)   
Space Complexity: O(1)