# Arrays

## Reverse an array

```text
void reverseArray(int arr[], int n)
{
    int low = 0, high = n - 1;
    while (low < high)
    {
        int temp = arr[low];
        arr[low] = arr[high];
        arr[high] = temp;
        low++;
        high--;
    }
}
```

## Remove Duplicates from a sorted array

```text
// input = [10, 20, 20, 30, 30, 30, 30]
// size = 7

// output = [10, 20, 30, _, _, _, _]
// size = 3

// Naive
int removeDuplicates(int arr[], int n)
{
    int temp[n];
    temp[0] = arr[0];
    int res = 1;
    for (int i = 1; i < n; i++)
    {
        if (temp[res - 1] != arr[i])
        {
            temp[res] = arr[i];
            res++;
        }
    }
    for (int i = 0; i < res; i++)
    {
        arr[i] = temp[i];
    }
    return res;
}

// Efficient space
int removeDuplicates(int arr[], int n)
{
    int res = 1;
    for (int i = 1; i < n; i++)
    {
        if (arr[i] != arr[res-1])
        {
            arr[res] = arr[i];
            res++;
        }
    }
    return res;
}
```

## Move Zeroes to End

```text
input = [0, 0, 10, 12, 0, 1,3]
output = [10, 12, 1, 3, 0, 0]

// Naive
void moveToEnd(int arr[], int n)
{
    for (int i = 0; i < n; i++)
    {
        if (arr[i] == 0)
        {
            for (int j = i + 1; j < n; j++)
            {
                if (arr[j] != 0)
                {
                    swap(arr[i], arr[j]);
                    break;
                }
            }
        }
    }
}

// Efficient space
void moveToEnd(int arr[], int n)
{
    int count = 0;
    for (int i = 1; i < n; i++)
    {
        if (arr[i] != 0)
        {
            swap(arr[i], arr[count]);
            count++;
        }
    }
}
```

## Left Rotate Array by one

```text
void rotateLeft(int arr[], int n)
{
    int temp = arr[0];
    for (int i = 1; i < n; i++)
    {
        arr[i-1] = arr[i];
    }
    arr[n-1] = temp;
}
```

## Left Rotate Array by D

```text
\\ Naive
void rotateLeftbyOne(int arr[], int n)
{
    int temp = arr[0];
    for (int i = 1; i < n; i++)
    {
        arr[i-1] = arr[i];
    }
    arr[n-1] = temp;
}

void leftRotate(int arr[], int n, int d)
{
    for (int i = 0; i < d; i++)
    {
        leftRotatebyOne(arr, n);
    }
}

// Efficient but extra space
void leftRotate(int arr[], int n, int d)
{
    int temp[d];
    for (int i = 0; i < d; i++)
    {
        temp[i] = arr[i];
    }
    for (int i = d; i < n; i++)
    {
        arr[i-d] = arr[i];
    }
    for (int i = 0; i < d; i++)
    {
        arr[n-d+i] = temp[i];
    }
}

// Most efficient
void reverse(int arr[], int low, int high)
    {
        while(low < high)
        {
            swap(arr[low], arr[high]);
            low++;
            high--;
        }
    }
void rotateArr(int arr[], int d, int n)
{
    reverse(arr, 0, d - 1);
    reverse(arr, d, n - 1);
    reverse(arr, 0, n - 1);
}
```

## Leader in an array

```text
// Naive
vector<int> leaders(vector<int> arr)
{
    vector<int> res;
    for (int i = 0; i < arr.size(); i++)
    {
        bool flag = false;
        for (int j = i + 1; j < arr.size(); j++)
        {
            if (arr[i] <= arr[j])
            {
                flag = true;
                break;
            }
        }
        if (flag == false)
            res.push_back(arr[i]);
    }
    return res;
}

// Efficient
vector<int> leaders(vector<int> arr)
{
    vector<int> res;
    n = arr.size()
    int curr = arr[n-1];
    res.push_back(arr[n-1]);
    for (int i = n - 2; i >= 0; i--)
    {
        if (curr < arr[i])
        {
            curr = arr[i];
            res.push_back(arr[i]);
        }
    }
    return res;
}
```

## Maximum difference in an array

```text
// Naive
int maxDiff(int arr[], int n)
{
    int res = arr[1] - arr[0];
    for (int i = 0; i < n - 1; i++)
    {
        for (int j = i + 1; j < n; j++)
        {
            res = max(res, arr[j] - arr[i]);
        }
    }
    return res;
}

// Efficient
int maxDiff(int arr[], int n)
{
    int res = arr[1] - arr[0];
    int minVal = arr[0];
    for (int i = 1; i < n; i++)
    {
        res = max(res, arr[i] - minVal);
        minVal = min(minVal, arr[i]);
    }
    return res;
}
```

### 6/5/21

## Frquencies in a Sorted Array

```text
void printFreq(int arr[], int n)
{
    int i = 1, freq = 1;
    while(i < n)
    {
        while(i < n && arr[i] == arr[i-1])
        {
            i++;
            freq++;
        }
        cout << arr[i] << " " << freq << endl;
        i++;
        freq = 1;
    }
    if (n == 1 || arr[n-1] != arr[n-2])
    {
        cout << arr[n-1] + " " + 1);
    }
}
```

## Stock Buy and Sell

```text
// Naive
int maxProfit(int price[], int start, int end)
{
    if (end <= start)
        return 0;
    int profit = 0, curr_profit = 0;
    for (int i = start; i < end; i++)
    {
        for (int j = i + 1; j <= n; j++)
        {
            curr_profit = price[j] - price[i] +
                            maxProfit(price, start, i - 1);
                            maxProfit(price, j + 1, end);
            profit = max(profit, curr_profit);
        }
    }
    return profit;
}

// Efficient

int maxProfit(int price[], int n)
{
    int profit = 0;
    for (int i = 1; i < n; i++)
    {
        if (price[i] > price[i-1])
        {
            profit += price[i] - price[i-1];
        }
    }
    return profit;
}
```

## Maximum consecutive 1s

```text
// Naive
int maxConsOnes(int arr[], int n)
{
    int res = 0;
    for (int i = 0; i < n; i++)
    {
        int curr = 0;
        for (int j = i; j < n; j++)
        {
            if (arr[j] == '1')
            {
                curr++;
            }
            else
            {
                break;
            }
        }
        res = max(res, curr);
    }
    return res;
}

// Efficient
int maxConsOnes(int arr[], int n)
{
    int res = 0, curr = 0;
    for (int i = 0; i < n; i++)
    {
        if (arr[i] == '0')
            curr = 0;
        else
        {
            curr++;
            res = max(res, curr);
        }
    }
    return res;
}
```

## Maximum Sub Array

```text
// Naive
int maxSubArray(int arr[], int n)
{
    int res = arr[0];
    for (int i = 0; i < n; i++)
    {
        int sum = 0;
        for (int j = 0; j < n; j++)
        {
            sum += arr[j];
            res = max(res, sum);
        }
    }
    return sum;
}

// Efficient - Kadane's Algorithm
int maxSubArray(int arr[], int n)
{
    int res = arr[0];
    int maxEnd = arr[0];
    for (int i = 1; i < n; i++)
    {
        maxEnd = max(maxEnd + arr[i], arr[i]);
        res = max(maxEnd, res);
    }
    return res;
}
```

### 7/5/21

## Trapping RainWater

```text
// Naive
int getWater(int arr[], int n)
{
    int res = 0;
    for (int i = 1; i < n-1; i++)
    {
        int lmax = 0;
        for (int j = 0; j < i; j++)
        {
            lmax = max(lmax, arr[j]);
        }
        int rmax = 0;
        for (int j = i+1; j < n; j++)
        {
            rmax = max(rmax, arr[j]);
        }
        res += (min(lmax, rmax) - arr[i]);
    }
    return res;
}

// Efficient
int getWater(int arr[], int n)
{
    int res = 0;
    int lmax[n], rmax[n];
    lmax[0] = arr[0];
    for (int i = 1; i < n; i++)
    {
        lmax[i] = max(arr[i], lmax[i-1]);
    }
    rmax[0] = arr[n-1];
    for (int i = n-2; i >= 0; i--)
    {
        rmax[i] = max(arr[i], rmax[i+1]);
    }
    for (int i = 1; i < n-1; i++)
    {
        res += (min(lmax[i], rmax[i]) - arr[i]);
    }
    return res;
}
```

### 13/5/21

## Maximum length even odd subarray \(Important\)

```text
// Naive
int maxEvenOdd(int arr[], int n)
{
    int res = 0;
    for(int i = 0; i < n; i++)
    {
        int curr = 0;
        for (int j = i + 1; j < n; j++)
        {
            if (arr[j] % 2 == 0 && arr[j-1] % 2 != 0) ||
                (arr[j] % 2 != 0 && arr[j-1] % 2 == 0)
            {
                curr++;
                res = max(curr, res);
            }
            else
            {
                break;
            }
        }
    }
    return res;
}

// Efficient - Kadane 
int maxEvenOdd(int arr[], int n)
{
    int curr = 1;
    int res = 1;
    for (int i = 1; i < n; i++)
    {
        if (arr[j] % 2 == 0 && arr[j-1] % 2 != 0) ||
                (arr[j] % 2 != 0 && arr[j-1] % 2 == 0)
        {
            curr++;
            res = max(curr, res);
        }
        else
        {
            curr = 1;
        }
    }
    return res;
}
```

## Maximum Circular Subarray sum

```text
// Naive
int maxCircularSum(int arr[], int n)
{
    int res = arr[0];
    for (int i = 0; i < n; i++)
    {
        int curr_max = res[i];
        int curr_sum = res[i];
        for (int j = 1; j < n; j++)
        {
            int index = (i + j) % n;
            curr_sum += arr[index];
            curr_max = max(curr_max, curr_sum);
        }
        res = max(curr_max, res);
    }
    return res;
}

// Efficient
int maxNormalSum(int arr[], int n)
{
    int res = arr[0];
    int maxEnd = arr[0];
    for (int i = 1; i < n; i++)
    {
        maxEnd = max(maxEnd + arr[i], arr[i]);
        res = max(maxEnd, res);
    }
    return res;
}

int maxCircularSum(int arr[], int n)
{
    int maxSum = maxNormalSum(arr, n);
    if (maxSum < 0)
    {
        return maxSum;
    }
    int arrSum = 0;
    // arrSum - minimum Sub Array
    for (int i = 0; i < n; i++)
    {
        arrSum += arr[i];
        arr[i] = -1 * arr[i];
    }
    int maxCircular = arrSum + maxNormalSum(arr, n);
    return max(maxSum, maxCircular)
}
```

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
Space Complexity: O\(1\)

