# Selection sort

## Arrays vs LinkedList

* Lists are better if you want to insert elements in the middle

| Type  | Arrays | Lists |
| ------------ |---------------| -----|
| Reading      | O(1) | O(n) |
| Insertion    | O(n) | O(1) |
| Deletion     | O(n) | O(1) |

* It’s worth mentioning that insertions and deletions are O(1) time only if you can instantly access the element to be deleted. It’s a common practice to keep track of the first and last items in a linked list, so it would take only O(1) time to delete those.
* Facebook uses a mix of both to store usernames
