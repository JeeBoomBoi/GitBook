# Day 5



**1\) Inversion of Array \(Using Merge Sort\)  We did different question lol**

[**https://www.youtube.com/watch?v=kQ1mJlwW-c0&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=10**](https://www.youtube.com/watch?v=kQ1mJlwW-c0&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=10)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution {
public:
    bool isIdealPermutation(vector<int>& A) {
        int n = A.size();
        for (int i = 0; i < n; i++)
        {
            if (abs(A[i] - i) > 1)
                return false;
        }
        return true;
    }
};
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

2\) **Stock Buy and Sell** 

[**https://www.youtube.com/watch?v=eMSfBgbiEjk&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=11**](https://www.youtube.com/watch?v=eMSfBgbiEjk&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=11)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution {
public:
    bool isIdealPermutation(vector<int>& A) {
        int n = A.size();
        for (int i = 0; i < n; i++)
        {
            if (abs(A[i] - i) > 1)
                return false;
        }
        return true;
    }
};
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

