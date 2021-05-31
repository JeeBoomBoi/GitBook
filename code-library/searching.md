# Searching

### 26/5/2021

## Binary Search
```cpp
#include<bits/stdc++.h>
using namespace std;

int binarySearch(int *arr, int n, int k)
{
    int low = 0;
    int high = n - 1;
    while (low <= high)
    {
        int mid = (low + high) / 2;
        if (arr[mid] == k)
            return mid;
        else if (arr[mid] > k)
            high = mid - 1;
        else
            low = mid + 1;
    }
    return -1;
}

int recursivebinarySearch(int *arr, int low, int high, int k)
{
    if (low > high)
        return -1;
    int mid = (low + high) / 2;
    if (arr[mid] == k)
        return mid;
    else if (arr[mid] > k)
        return recursivebinarySearch(arr, low, mid - 1, k);
    else
        return recursivebinarySearch(arr, mid + 1, high, k);
}


int main()
{
    int arr[] = {1,2,3,4,5,6};
    int size = 6;
    int search = 5;
    cout << binarySearch(arr, size, search) << endl;
}
```

## First Occurence
```cpp
#include<bits/stdc++.h>
using namespace std;

// recursive
int firstOccurence(int *arr, int low, int high, int x)
{
    if (low > high)
        return -1;
    int mid = (low + high) / 2;
    if (arr[mid] > x)
        return firstOccurence(arr, low, mid - 1, x);
    else if (arr[mid] < x)
        return firstOccurence(arr, mid + 1, high, x);
    else
    {
        if (mid == 0 || arr[mid - 1] != arr[mid])
            return mid;
        else
            return firstOccurence(arr, low, mid - 1, x);
    }
}

// iterative
int firstOccurence(int *arr, int n, int x)
{
    int low = 0;
    int high = n - 1;
    while(low <= high)
    {
        int mid = (low + high) / 2;
        if (arr[mid] > x)
            high = mid - 1;
        else if (arr[mid] < x)
            low = mid + 1;
        else
        {
            if (mid == 0 || arr[mid] != arr[mid - 1])
                return mid;
            else
                high = mid - 1;
        }
    }
    return -1;
}

int main()
{
    int arr[] = {1, 5, 5, 10, 10, 10, 20, 20, 30};
    cout << firstOccurence(arr, 0, 8, 10) << endl;
}
```

### 29/5/2021

## Last Occurence
```cpp
#include<bits/stdc++.h>
using namespace std;

int rlastOccurence(int *arr, int low, int high, int x, int n)
{
    if (low > high)
        return -1;
    int mid = (low + high) / 2;
    if (arr[mid] > x)
        return rlastOccurence(arr, low, mid - 1, x, n);
    else if (arr[mid] < x)
        return rlastOccurence(arr, mid + 1, high, x, n);
    else
    {
        if (mid == n - 1 || arr[mid] != arr[mid+1])
            return mid;
        else
            return rlastOccurence(arr, mid + 1, high, x, n);
    }
}

int lastOccurence(int *arr, int n, int x)
{
    int low = 0;
    int high = n - 1;
    while(low <= high)
    {
        int mid = (low + high) / 2;
        if (arr[mid] > x)
            high = mid - 1;
        else if (arr[mid] < x)
            low = mid + 1;
        else
        {
            if (mid == n - 1 || arr[mid] != arr[mid + 1])
                return mid;
            else
                low = mid + 1;
        }
    }
    return -1;
}

int main()
{
    int arr[] = {1, 5, 5, 10, 10, 10, 20, 20, 30};
    // cout << rlastOccurence(arr, 0, 9, 10, 9) << endl;
    cout << lastOccurence(arr, 9, 10) << endl;
}
```  

## Count Occurence
```cpp
#include<bits/stdc++.h>
using namespace std;

int firstOccurence(int *arr, int n, int x)
{
    int low = 0;
    int high = n - 1;
    while(low <= high)
    {
        int mid = (low + high) / 2;
        if (arr[mid] > x)
            high = mid - 1;
        else if (arr[mid] < x)
            low = mid + 1;
        else
        {
            if (mid == 0 || arr[mid] != arr[mid - 1])
                return mid;
            else
                high = mid - 1;
        }
    }
    return -1;
}

int lastOccurence(int *arr, int n, int x)
{
    int low = 0;
    int high = n - 1;
    while(low <= high)
    {
        int mid = (low + high) / 2;
        if (arr[mid] > x)
            high = mid - 1;
        else if (arr[mid] < x)
            low = mid + 1;
        else
        {
            if (mid == n - 1 || arr[mid] != arr[mid + 1])
                return mid;
            else
                low = mid + 1;
        }
    }
    return -1;
}

int countOccurence(int *arr, int n, int x)
{
    int first = firstOccurence(arr, n, x);
    int last = lastOccurence(arr, n, x);
    if (first == -1)
        return 0;
    else
        return last - first + 1;
}

int main()
{
    int arr[] = {1, 5, 5, 10, 10, 10, 20, 20, 30};
    cout << countOccurence(arr, 9, 10) << endl;
}
```

## Count Ones in Sorted
```cpp
#include<bits/stdc++.h>
using namespace std;

int countOnes(int *arr, int n)
{
    int low = 0;
    int high = n - 1;
    while(low <= high)
    {
        int mid = (low + high) / 2;
        if (arr[mid] == 0)
            low = mid + 1;
        else
        {
            if (arr[mid] == 1 || arr[mid - 1] == 0)
            {   
                return n - mid;
            }
            else
            {
                high = mid - 1;
            }
        }
    }
    return 0;
}

int main()
{
    int arr[] = {0,0,0,1,1,1,1,1};
    cout << countOnes(arr, 8) << endl;
}
```

## Square Root
```cpp
#include<bits/stdc++.h>
using namespace std;

int squareRoot(int x)
{
    int low = 1;
    int high = x;
    int ans = -1;
    while(low <= high)
    {
        int mid = (low + high) / 2;
        int midSquare = mid * mid;
        if (midSquare == x)
            return mid;
        else if (midSquare > x)
            high = mid - 1;
        else
        {
            low = mid + 1;
            ans = mid;
        }
    }
    return ans;
}

int main()
{
    int num;
    cin >> num;
    cout << squareRoot(num) << endl;
}
```

## Search Infinite Sized Array
```cpp
#include<bits/stdc++.h>
using namespace std;

int binarySearch(int *arr, int low, int high, int x)
{
    while(low <= high)
    {
        int mid = (low + high) / 2;
        if (arr[mid] == x)
            return mid;
        else if(arr[mid] > x)
            high = mid - 1;
        else
            low = mid + 1;
    }
    return -1;
}


int search(int *arr, int x)
{
    if(arr[0] == x)
        return 0;
    int i = 1;
    while(arr[i] < x)
        i = i * i;
    if(arr[i] == x)
        return i;
    
    return binarySearch(arr, i/2 + 1, i - 1, x);
}  
```

### 30/5/21

## Search in Sorted Rotated Array
```cpp
#include<bits/stdc++.h>
using namespace std;

int search(int arr[], int n, int x)
{
    int low = 0;
    int high = n - 1;
    while(low <= high)
    {
        int mid = (low + high) / 2;
        if (arr[mid] == x)
            return mid;
        
        if (arr[low] < arr[mid])
        {
            if (x >= arr[low] && x < arr[mid])
                high = mid - 1;
            else
                low = mid + 1;
        }
        else
        {
            if (x > arr[mid] && x <= arr[high])
                low = mid + 1;
            else
                high = mid - 1;
        }
    }
    return -1;
}

int main()
{
    int arr[] = {10, 20, 40, 60, 5, 8};
    cout << search(arr, 6, 5) << endl;
}
```

## Find a Peak Element
```cpp
#include<bits/stdc++.h>
using namespace std;

int getaPeak(int arr[], int n)
{
    int low = 0;
    int high = n - 1;
    while(low <= high)
    {
        int mid = (low + high) / 2;
        if ((mid == 0 || arr[mid - 1] <= arr[mid]) && (mid == n - 1 || arr[mid + 1] <= arr[mid]))
            return arr[mid];
        else
        {
            if (mid > 0 && arr[mid - 1] >= arr[mid])
            {
                high = mid - 1;
            }
            else
            {
                low = mid + 1;
            }
        }
    }
    return -1;
}

int main()
{
    int arr[] = {5, 20, 40, 30, 20, 50, 60};
    cout << getaPeak(arr,7) << endl;
}
```

### 31/5/21

## Two Pointer Approach
```cpp
#include<bits/stdc++.h>
using namespace std;

bool isPair(int arr[], int n, int x)
{
    int left = 0;
    int right = n - 1;
    while(left < right)
    {
        if (arr[left] + arr[right] == x)
            return true;
        else if (arr[left] + arr[right] < x)
            left++;
        else
            right--;
    }
    return false;
}

int main()
{
    int arr[] = {2,3,4,6,8,10,12,14};
    cout << isPair(arr, 8, 28) << endl;
}
```

## Finding Triplets
```cpp
#include<bits/stdc++.h>
using namespace std;

bool isPair(int arr[], int left, int right, int x)
{
    while(left < right)
    {
        if (arr[left] + arr[right] == x)
            return true;
        else if (arr[left] + arr[right] < x)
            left++;
        else
            right--;
    }
    return false;
}

bool isTriplet(int arr[], int n, int x)
{
    for (int i = 0; i < n; i++)
    {
        return isPair(arr, i + 1, n - 1, x - arr[i]);
    }
    return false;
}

int main()
{
    int arr[] = {1,2,3,4,5,6,7,8};
    cout << isTriplet(arr, 8, 15) << endl;
}
```

## Median of two Sorted Arrays
```cpp
#include<bits/stdc++.h>
using namespace std;

double getMedian(int a1[], int a2[], int n1, int n2)
{
    if (n1 > n2)
    {
        swap(a1, a2);
        swap(n1, n2);
    }
    int begin = 0;
    int end = n1 - 1;
    while(begin <= end)
    {
        int i1 = (begin + end) / 2;
        int i2 = (n1 + n2 + 1) / 2 - i1;

        int min1 = (i1 == n1) ? INT_MAX : a1[i1];
        int max1 = (i1 == 0) ? INT_MIN : a1[i1 - 1];

        int min2 = (i2 == n2) ? INT_MAX : a2[i2];
        int max2 = (i2 == 0) ? INT_MIN : a2[i2 - 1];

        if (max1 <= min2 && max2 <= min1)
        {
            if ((n1 + n2) % 2 == 0)
                return ((double) max(max1, max2) + min(min1, min2)) / 2;
            else
                return (double) max(max1, max2); 
        }
        else if(max1 > min2)
            end = i1 - 1;
        else
            begin = i1 + 1;
    }
}

int main()
{
    int a1[] = {30, 40, 50, 60};
    int a2[] = {5, 6, 7, 8, 9};
    cout << getMedian(a1, a2, 4, 5) << endl;
}
```