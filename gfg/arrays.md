# Arrays

**16. Rearrange Array Alternately**  
Problem link: [link](https://t.ly/2iSm)
{% tabs %}
{% tab title="CPP" %}
```
// Naive
void rearrange(long long *arr, int n) 
    { 
    	
    	// Your code here
    	long long temp;
    	for (int i = 0; i < n; i++)
    	{
    	    if (i % 2 == 0)
    	    {
    	        temp = arr[n-1];
    	        for (int j = n - 2; j >= i; j--)
    	        {
    	            arr[j+1] = arr[j];
    	        }
    	        arr[i] = temp;
    	    }
    	}
    }
// Efficient

```
{% endtab %}

{% tab title="Python" %}
```

```
{% endtab %}
{% endtabs %}

Time Complexity : O()   
Space Complexity: O()