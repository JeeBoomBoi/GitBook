## Reverse an array

```
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

```
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
```
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

```
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

```
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

# Leader in an array

```
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