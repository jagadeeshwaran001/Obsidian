[[HashMap]] is a [[java]] [[collections]] framework and implements the [[computer science/full stack develpment/java/Map|Map]] [[interface]]. it allows for storing key-value pairs where each key is unique.

## Key Features.

1. **Constant-[[Time Complexity]]**: The average time complexity for basic operations like insertion, deletion, and lookup is `O(1)`, making `HashMap` very fast.
2. **Unordered**: Unlike some other collections like `TreeMap`, `HashMap` does not guarantee any order of keys or values.
3. **Allows Null**: `HashMap` allows one null key and multiple null values.
4. **Not [[Thread-safe]]**: If multiple threads access a `HashMap` concurrently and modify it, external synchronization is needed.

Internally, [[HashMap]] uses an array of buckets where each bucket is [[Linked List]] from [[java 8]] onwards.

When we add a key-value pair in the [[HashMap]]  [[hash value]] for the keys is computed to determine which bucket the pair will be stored in.

## Internal Mechanism

1. Hashing: When you insert a key-value pair, the key's `hashcode()` method is used to compute a hash code (an integer). This hash code is then used to determine the index of the bucket (array position) where the key-value pair should be stored.

```java
int hashCode = key.hashCode();
int bucketIndex = hashCode % capacity; // capacity is the size of the bucket array
```

3. **Collision Handling**: A hash collision happens when two different keys have the same hash code, meaning they end up in the same bucket. In this case, Java uses a `LinkedList` to store multiple key-value pairs in the same bucket. From Java 8 onward, if the list in the bucket exceeds a certain threshold (typically 8), the list is converted to a balanced **binary tree** to improve performance.
4. **resize()**: If the `HashMap` becomes too full, it automatically resizes itself by increasing the capacity of the array (usually doubling it) and redistributing the entries (rehashing). The resizing process can be expensive, which is why it’s important to set an appropriate initial capacity if you know the number of entries in advance.
### Important Parameters:

1. **Initial Capacity**: The initial size of the bucket array. By default, it is 16.
2. **Load Factor**: This controls how full the `HashMap` can get before it resizes. The default load factor is 0.75, meaning the `HashMap` will resize when 75% of its capacity is filled.
```java
HashMap<String, Integer> map = new HashMap<>(16, 0.75f);
map.put("John", 25);
map.put("Doe", 30);

int age = map.get("John");  // Returns 25
```

### Java 8 Optimizations:

- **Treeify**: From [[java 8]] onward, if a bucket’s linked list grows beyond 8 elements, it is transformed into a balanced binary tree (Red-Black Tree) to improve retrieval time from O(n) to O(log n).
- **Untreeify**: If the tree shrinks below a threshold, it is converted back into a linked list.