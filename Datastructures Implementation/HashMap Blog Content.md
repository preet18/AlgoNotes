Introduction about HashMap
Properties and methods on HashMap
Internal working of HashMap
Implementation of HashMap in Java.
Explanation of the implementation.

### Introduction about HashMap
HashMap is a data structure which stores the data in key-value format. The time taken to retrieve a value based on key is O(1) in the best case and O(N) in worst case. In Java HashMap implements Map.

### Properties of HashMap
It allows null value and null key.
It's an unordered collection i.e it doesn't guarantee any specific order of the elements
It's not thread-safe and synchronization of concurrent modifications to the hashmap need to done explicity.

### The Important methods of HashMap
put()
get()
entrySet()
keySet()
values()
size()
isEmpty()
containsKey()
containsValue()

### Syncronised HashMap
As hashmap is unsynchronized, multiple threads can access it simultaneously which may result in inconsistency. To avoid this problem, we need to synchronize it externally.
Synchronization can be done externally in two ways.
1. Using "Synchronized" keyword
2. By wrapping around Collections.synchronizedMap()

### Internal working of HashMap
HashMap consists of the follwoing 4 parameters mainly.
1. int hash
2. K key
3. V value
4. Node next

#### Performance of HashMap
1. Initial Capacity
2. Load Factor

1. Initial Capacity
It is the capacity of hashMap instance when it's created.

2. Load Factor
It's the measure when rehashing should be done. Rehashing is the process of increasing capacity.

In HashMap capacity is increased two times during rehashing. Preferred load factor value is 0.75 and it lies in between 0 to 1.

#### Hashing 
It is the process of converting an object into integers form by using the method hashCode().
hashCode() should be written properly for better performance of HashMap. It is used to calculate the bucket i.e to calculate the index. It returns the memory reference of the object in the integer form.



