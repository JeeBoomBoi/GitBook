## Check power of 2

```
bool isPowerofTwo(long long n)
{

    // Your code here
    if (n == 0)
        return false;
    return ((n & (n - 1)) == 0);
}
```

## Count set bits

```
#include<bits/stdc++.h>

// naive approach - O'(total number of bits)
int countSet(int n)
{
    int res = 0;
    while (n > 0)
    {
        if ((n & 1) == 1) // res = res + (n & 1)
            res++;
        n = n >> 1;
    }
    cout << res << endl;
}


//  brian kerningam's algo (standard) - O'(number of set bits)
int countSet1(int n)
{
    int res = 0; 
    while (n >  0)
    {
        n = (n & (n - 1))
        res++;
    }
    return res;
}

// using a look up table 
int table[256];
void initialize()
{
    table[0] = 0;
    for (int i = 1; i < 256; i++)
    {
        table[i] = (i & 1) + table[i / 2];
    }
}

int count(int n)
{
    int res = table[n & 0xff];
    n = n >> 8;
    res += table[n & 0xff];
    n = n >> 8;
    res += table[n & 0xff];
    n = n >> 8;
    res += table[n & 0xff];
    n = n >> 8;
    return res;
}
```

## Find missing number in an array

```
// Find the missing number in the array
int missingNumber(vector<int> &nums)
{
    int x = 0, y = 0;
    for (int i = 0; i < nums.size(); i++)
    {
        x = x ^ nums[i];
        y = y ^ (i + 1);
    }
    return x ^ y;
}

```

## Odd one occurring

```
// Odd one occuring
int oddOne(int arr[], int n)
{
    int res = 0;
    for (int i = 0; i < n; i++)
    {
        res = res ^ arr[i];
    }
    return res;
}
```

## Two odd occurring

```
vector<int> twoOddNum(int arr[], int n)
{
    // code here
    int Xor = 0, res1 = 0, res2 = 0;
    for (int i = 0; i < n; i++)
    {
        Xor = Xor ^ arr[i];
    }
    int s = Xor & ~(Xor - 1);
    for (int i = 0; i < n; i++)
    {
        if ((arr[i] & s) != 0)
            res1 = res1 ^ arr[i];
        else
            res2 = res2 ^ arr[i];
    }
    vector<int> res;
    if (res2 > res1)
    {
        res.push_back(res2);
        res.push_back(res1);
    }
    else
    {
        res.push_back(res1);
        res.push_back(res2);
    }
    return res;
}
```