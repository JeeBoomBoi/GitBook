# Strings

## Check Palindrome
```cpp
#include <iostream>
using namespace std;

bool checkPalindrome(string &s) {
    int low = 0;
    int high = s.length() - 1;
    while (low < high) {
        if (s[low] != s[high]) {
            return false;
        }
        low++;
        high--;
    }
    return true;
}

int main() {
	string s = "malayalam";
	cout << checkPalindrome(s) << endl;
	return 0;
}
```

## Check if a String is a Subsequence of Other
```cpp
#include <iostream>
using namespace std;

// A subsequence is a sequence of characters from another string
// The order of character should be followed in the sequence
bool isSubSequence(string &s1, string &s2) {
    int n = s1.length();
    int m = s2.length();
    
    if (n < m) return false;
    
    int j = 0;
    for (int i = 0; i < n && j < m; i++) {
        if (s1[i] == s2[j])
            j++;
    }
    return (j == m);
}

int main() {
	string s1 = "malayalam";
	string s2 = "aya";
	cout << isSubSequence(s1, s2) << endl;
	return 0;
}
```

## Check for Anagram 

```cpp
#include <iostream>
using namespace std;

const int CHAR = 256;

// a word or phrase that is made by arranging the letters of another word or phrase in a different order.
// "listen" "silent"
bool anagram(const string &s1, const string &s2) {
    if (s1.length() != s2.length())
        return false;
        
    int n = s1.length();
    int arr[CHAR] = {0};
    
    for (int i = 0; i < n; i++) {
        arr[s1[i]]++;
        arr[s2[i]]--;
    }
    
    for (int i = 0; i < CHAR; i++) {
        if (arr[i] != 0) 
            return false;
    }
    
    return true;
}

int main() {
	string s1 = "malayalam";
	string s2 = "ayamalmal";
	cout << anagram(s1, s2) << endl;
	return 0;
}
```

