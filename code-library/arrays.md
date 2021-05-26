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
 Naive
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
    rmax[n-1] = arr[n-1];
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

## Maximum length even odd subarray (Important)

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

## Majority Elements
```
int findMajority(int arr[], int n)
{
    for(int i = 0; i < n; i++)
    {
        int count = 1;
        for (int j = i + 1; i < n; i++)
        {
            if (arr[i] == arr[j])
                count++;
        }
        if (count > n / 2)
        {
            return i;
        }
    }
    return -1;
}

// Efficient
// moore voting algorithm
int findMajority(int arr[], int n)
{
    int res = 0;
    int count = 1;
    for (int i = 0; i < n; i++)
    {
        if (arr[res] == arr[i])
            count++;
        else
            count--;

        if (count == 0)
        {
            res = i;
            count = 1;
        }
    }

    count = 0;
    for (int i = 0; i < n; i++)
    {
        if (arr[res] == arr[i])
            count++;
    }
    if (count <= n/2)
        return -1;
    return res;
}
```

## Minimum Consecutive Flips

```
void printGroups(int arr, int n)
{
    // flip the 2nd group always
    for (int i = 1; i < n; i++)
    {
        if (arr[i] != arr[i-1])
        {
            if (arr[i] != arr[0])
                cout << "From " << i << "to ";
            else
                cout << i - 1 << endl;
        }
    }

    if (arr[n-1] != arr[0])
        cout << n - 1 << endl;
}
```

## Maximum sum of K Consecutive elements (Sliding window)
```
// Naive O((n-k) * k)
int slideSum(int arr[], int n, int k)
{
    int max_sum = INT_MIN;
    for (int i = 0; i + k - 1< n; i++)
    {
        int sum = 0;
        for (int j = 0; j < k; j++)
        {
            sum += arr[i + j];
        }
        max_sum = max(max_sum, sum);
    }
    return max_sum;
}

int slideSum(int arr[], int n, int k)
{
    int curr_sum = 0;
    for (int i = 0; i < k; i++)
    {
        curr_sum += arr[i];
    }
    int max_sum = curr_sum;
    for (int i = k; i < n; i++)
    {
        curr_sum += (arr[i] - arr[i-k]);
        max_sum = max(max_sum, curr_sum);
    }
    return max_sum;
}
```

## Subarray with given sum
```
// only works for non negative numbers
bool isSubPresent(int arr[], int n, int sum)
{
    int curr_sum = arr[0];
    int start = 0;
    for (int end = 1; end < n; end++)
    {
        while(curr_sum > sum && start < end - 1)
        {
            curr_sum -= arr[start];
            start++;
        }
        if (curr_sum == sum)
            return true;
        if (curr_sum < sum)
            curr_sum += arr[end];
    }
    return (curr_sum == sum);
}
```

### 14/5/21

## Prefix Sum
```
// Build prefix sum array
int* makePrefixArr(int arr[], int n)
{
    for(int i = 1; i < n; i++)
    {
        arr[i] = arr[i] + arr[i-1];
    }
    return arr;
}

int getSum(int arr[], int l, int m)
{
    if (l != 0)
        return arr[r] - arr[l-1];
    else
        return arr[r];
}

int main() {
    // Write C++ code here
    int arr[] = {1,2,3,4,5};
    int *a = makePrefixArr(arr, 5);
    int l, r;
    cin >> l >> r;
    cout << getSum(a, l, r);
    return 0;
}
```

## Equlibrium Point
```
int equli(int arr[], int n)
{
    int l_sum = 0, r_sum = 0;
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < i; j++)
            l_sum += arr[j];
        for (int k = i + 1; k < n; k++)
            r_sim += arr[k];
        if (l_sum == r_sum)
            return i;
    }
    return -1;
}

bool isEqPoint(int arr[], int n)
{
    int sum = 0;
    for (int i = 0; i < n; i++)
    {
        sum += arr[i];
    }
    int l_sum = 0;
    for (int i = 0; i < n; i++)
    {
        if (l_sum == sum - arr[i])
            return true;
        l_sum += arr[i];
        sum -= arr[i];
    }
    return false;
}
```

### 15/5/21

## Maximum appearing element in the given ranges

```
int maxOccur(int l[], int r[], int n)
{
    vector<int> arr[1000];
    for (int i = 0; i < n; i++)
    {
        arr[l[i]]++;
        arr[r[i] + 1]--;
    }
    int maxi = arr[0];
    int res = 0;
    for (int i = 1; i < 1000; i++)
    {
        arr[i] += arr[i-1];
        if (maxi <  arr[i])
        {
            maxi = arr[i];
            res = i;
        }
    }
    return res;
}
```