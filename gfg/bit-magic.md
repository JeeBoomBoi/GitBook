# Bit Magic

**1. Find first set bit**  
Problem link: [link](https://t.ly/1K0c)

{% tabs %}
{% tab title="CPP" %}
```text
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
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(log\(n\)\)  
Space Complexity: O\(n\)

**2. Rightmost different bit**  
Problem link: [link](https://t.ly/w7ii)

{% tabs %}
{% tab title="CPP" %}
```text
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
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(max\(log m, log n\)\)  
Space Complexity: O\(1\)

**3. Check whether K-th bit is set or not**  
Problem link: [link](https://t.ly/4qFH)

{% tabs %}
{% tab title="CPP" %}
```text
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
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(log n\)  
Space Complexity: O\(1\)

**4. Count total set bits**  
Problem link: [link](https://t.ly/SS91)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution{
    public:
    // n: input to count the number of set bits
    //Function to return sum of count of set bits in the integers from 1 to n.
    int countSetBits(int N)
    {
        // Your logic here
        int res = 0;
        int two = 2;
        int n = N;
        while (n)
        {
            res += (N / two) * (two >> 1);
            if ((N & (two - 1)) > (two >> 1) - 1)
                res += (N & (two - 1)) - (two >> 1) + 1;
            two <<= 1;
            n >>= 1;
        }
        return res;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(log N\)  
Space Complexity: O\(1\)

**5. Bit Difference**  
Problem link: [link](https://t.ly/SCcs)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution{
    public:
    // Function to find number of bits needed to be flipped to convert A to B
    int countBitsFlip(int a, int b){

        // Your logic here
        int count = 0;
        while(a != 0 || b != 0)
        {
            int c = a & 1;
            int d = b & 1;
            if (c != d)
                count++;
            a = a >> 1;
            b = b >> 1;
        }
        return count;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(log N\)  
Space Complexity: O\(1\)

**6. Number is sparse or not**  
Problem link: [link](https://t.ly/YNC1)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution{
    public:
    // function to check if the number is sparse
    // n : is the number to check if it is sparse
    bool isSparse(int n){

        // Your code
        int c = 0;
        while (n != 0)
        {
            int t = n & 1;
            if (t == 1)
                c++;
            else
                c = 0;
            if (c >= 2)
                return false;
            n = n >> 1;
        }
        return true;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(log N\)  
Space Complexity: O\(1\)

**7. Longest Consecutive 1's**  
Problem link: [link](https://t.ly/psO5)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution
{
    public:
    int maxConsecutiveOnes(int n)
    {
        // code here
        int count = 0;
        int m = 0;
        while(n != 0)
        {
            if (n & 1)
            {
                count++;
                m = max(m, count); 
            }
            else
            {
                count = 0;
            }
            n = n >> 1;
        }
        return m;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(log N\)  
Space Complexity: O\(1\)

**8. Binary To Gray Code equivalent**  
Problem link: [link](https://t.ly/qzC1)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution{
    public:
    //  Function to find the gray code of given number n
    int greyConverter(int n)
    {

        // Your code here
        return n ^ (n >> 1);
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(1\)  
Space Complexity: O\(1\)

**9. Gray to Binary equivalent**  
Problem link: [link](https://t.ly/vvAD)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution{

    // function to convert a given Gray equivalent n to Binary equivalent.
    public:
    int grayToBinary(int n)
    {

        // Your code here
        int num = n;
        while (n >= 1)
        {
            n = n >> 1;
            num = num ^ n;
        }
        return num;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(log N\)  
Space Complexity: O\(1\)

**10. Power of 2**  
Problem link: [link](https://t.ly/t6JR)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution{
    public:
    // Function to check if given number n is a power of two.
    bool isPowerofTwo(long long n){

        // Your code here    
        if (n == 0)
            return false;
        return ((n & (n - 1)) == 0);

    }
};
```
{% endtab %}

{% tab title="Python" %}
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(log N\)  
Space Complexity: O\(1\)

**11. Swap all odd and even bits**  
Problem link: [link](https://t.ly/YC11)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution{
    public:
    // function to swap odd and even bits
    unsigned int swapBits(unsigned int n)
    {

        // Your code here
        int even = (n & 0xAAAAAAAA);
        int odd = (n & 0x55555555);
        even = even >> 1;
        odd = odd << 1;
        int out = (even | odd);
        return out;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(1\)  
Space Complexity: O\(1\)

**12. Maximum AND Value**  
Problem link: [link](https://t.ly/7YR0)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution
{
    public:
    // Function for finding maximum AND value.
    int checkbit(int pattern, int arr[], int n)
    {
        int count = 0;
        for (int i = 0; i < n; i++)
        {
            if ((pattern & arr[i]) == pattern)
                count++;
        }
        return count;
    }
    int maxAND (int arr[], int n)
    {
        // Your code here
        int res = 0;
        int count;
        for (int bit = 31; bit >= 0; bit--)
        {
            count = checkbit(res | (1 << bit), arr, n);

            if(count >= 2)
                res |= 1 << bit;
        }
        return res;
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text

```
{% endtab %}
{% endtabs %}

Time Complexity : O\(N \* log M\)  
Space Complexity: O\(1\)

