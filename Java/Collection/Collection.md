![[Screenshot 2024-08-26 184623.png]]
# Topics
1. ArrayList
2. HashSet
	- HashSet is a collection of unique values
	- There is no concept of index in a HashSet
	- There is no particular order in which the values are stored in a HashSet
3. TreeSet
	- Values are stored in sorted fashion
	- TreeSet extends AbstractSet and implements NavigableSet which extends SortedSet
4. Map -- It is not part of Collection Interface
5. HashSet
	- HashSet cannot contain duplicate values.
	- HashSet allows `null` value.
    - HashSet is an unordered collection. It does not maintain the order in which the elements are inserted.
    - HashSet internally uses a [HashMap](https://www.callicoder.com/java-hashmap/) to store its elements.
    - HashSet is not thread-safe. If multiple threads try to modify a HashSet at the same time, then the final outcome is not-deterministic. You must explicitly synchronize concurrent access to a HashSet in a multi-threaded environment.
