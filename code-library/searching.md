# Searching

### 26/5/2021

## Binary Search
```
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
```
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
```
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
```
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
```
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
```
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
```
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

