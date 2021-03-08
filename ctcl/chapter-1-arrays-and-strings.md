# Chapter 1 Arrays and Strings

Date: 1/2/2021

1\) Is Unique: Implement an algorithm to determine if a string has all unique characters. What if you cannot use additional data structures ?

{% tabs %}
{% tab title="Python" %}
```text
def IsUnique(string):
    # to make sure a character is unique (ASCII)
    if len(string) > 128:
        return False
        
    char_set = [False for _ in range(128)]
    for char in string:
        asc = ord(char)
        if char_set[asc]:
            return False
        
        char_set[asc] = True
        
    return True
```
{% endtab %}

{% tab title="CPP" %}
```text
bool isUnique(const string &str) 
{
    if (str.length() > 128) 
    {
        return false;
    }
    vector<bool> char_set(128);
    for (int i = 0; i < str.length(); i++)
    {
        int val = str[i];
        if (char_set[val] == true) 
        {
            return false;
        }
        char_set[val] = true;
    }
    return true;
}
```
{% endtab %}
{% endtabs %}

Date: 2/2/2021

2\) Check Permutation: Given 2 strings, write a method to decide if one is a permutation of the other.

{% tabs %}
{% tab title="Python" %}
```text
def checkPermutationUsingSort(str1, str2):
    if len(str1) != len(str2):
        return False
    s1, s2 = sorted(str1), sorted(s2)
    for i in range(len(s1)):
        if s1[i] != s2[i]:
            return False

    return True
        
    
def checkPermutation(str1, str2):
    if len(str1) != len(str2):
        return False
    
    counter = [0] * 256
    for char in str1:
        counter[ord(char)] += 1
    for char in str2:
        if counter[ord(char)] == 0:
            return False
        counter[ord(char)] -= 1
    return True
```
{% endtab %}

{% tab title="CPP" %}
```text
#include<bits/stdc++.h>
using namespace std;

bool checkPermutationSort(string str1, string str2)
{
    if(str1.length() != str2.length())
        return false;

    sort(str1.begin(), str1.end());
    sort(str2.begin(), str2.end());

    for (int i = 0; i < str1.length(); i++)
    {
        if (str1[i] != str2[i])
        {
            return false;
        }
    }
    return true;
}

bool checkPermutation(string str1, string str2)
{
    if (str1.length() != str2.length())
        return false;
    
    int counter[256] = {0};
    for (int i = 0; i < str1.length(); i++)
    {
        int val = str1[i];
        counter[val] += 1;
    }
    for (int j = 0; j < str2.length(); j++)
    {
        int val = str2[j];
        if (counter[val] == false)
        {
            return false;
        }
        counter[val] -= 1;
    }

    return true;
}
```
{% endtab %}
{% endtabs %}

3\) URLify : Write a method to replace all spaces in a string with "%20"

{% tabs %}
{% tab title="Python" %}
```text
def URLifyPythonic(string, length):
    return string.rstrinp().replace(" ", "%20")

def URLify(string, length):
    char_list = list(string)
    string = ""
    new_index = len(char_list)

    for i in reversed(range(length)):
        if char_list[i] == " ":
            char_list[new_index - 3 : new_index] = "%20"
            new_index -= 3
        else:
            char_list[new_index - 1] = char_list[i]
            new_index -= 1

    return string.join(char_list)

print(URLify("Mr John Smith    ", 13))
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

