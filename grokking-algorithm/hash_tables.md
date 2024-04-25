# Hash tables

# Implementation
{% tabs %}
{% tab title="Java" %}
```java
package snips;
import java.util.HashMap;

public class HashMapImplementation {
    public static void main(String[] args) {
        HashMap <String, Float> hashMap = new HashMap<String, Float>();
        hashMap.put("Apple", Float.valueOf("0.67"));
        hashMap.put("milk", Float.valueOf("1.48"));
        hashMap.put("avacado", Float.valueOf("1.49"));
        for (String x: hashMap.keySet()) {
            System.out.println(x);
        }
        for (Float y: hashMap.values()) {
            System.out.println(y);
        }
        System.out.println(hashMap.size());
        System.out.println(hashMap.containsKey("apple"));
        System.out.println(hashMap.getOrDefault("Apple", Float.valueOf(0)));
    }
}
```
{% endtab %}

* Insert, Read and Delete
  * Average case : O(1)
  * Worst case : O(n)
* Look at the average case for hash tables. Hash tables are as fast as arrays at searching (getting a value at an index). And they’re as fast as linked lists at inserts and deletes. It’s the best of both worlds! But in the worst case, hash tables are slow at all of those. So it’s important that you don’t hit worst-case performance with hash tables. And to do that, you need to avoid collisions. To avoid collisions, you need
  * A low load factor
  * A good hash function


## Chapter Recap
* You’ll almost never have to implement a hash table yourself. The programming language you use should provide an implementation for you. You can use Python’s hash tables and assume that you’ll get the average-case performance: constant time.

* Hash tables are a powerful data structure because they’re so fast and they let you model data in a different way. You might soon find that you’re using them all the time.

* You can make a hash table by combining a hash function with an array.

* Collisions are bad. You need a hash function that minimizes collisions.

* Hash tables have really fast search, insert, and delete.

* Hash tables are good for modeling relationships from one item to another item.

* Once your load factor is greater than 0.7, it’s time to resize your hash table.

* Hash tables are used for caching data (for example, with a web server).

* Hash tables are great for catching duplicates.
