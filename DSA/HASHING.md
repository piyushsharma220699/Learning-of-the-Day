Hashing is a technique used in computer science to map data of arbitrary size to fixed-size values. The resulting fixed-size values are called hashes, and they represent the original data in a highly compressed format.

It is is a fundamental concept in computer science, and it is implemented in many programming languages, including C++, Python, and Java.

**C++ : (unordered_map)** In C++, you can use the standard template library (STL) to implement hashing.
**Python : (Dictionary)** In Python, hashing is implemented through built-in hash functions, such as `hash()`.
**Java : (HashMap)** In Java, you can use the built-in `hashCode()` method to compute the hash code of an object.

**There are Key - Value pairs. but you are NOT ALLOWED TO PUT EVERY DATATYPE AS KEY.**

- For some native type of keys, this hashing function is internally implemented by the language, for others, you're given an option to implement the hashing function which can spit out an integer for the object specified. Eg: In Python, KEY can't be a list, but there is a way to define that.

![[WhatsApp Image 2023-05-04 at 05.30.38.jpg]]
<h2>WHY A COMPRESSION FUNCTION IS REQUIRED DURING HASHING?</h2>
- Compression Function is just a \[0,N\) --> \[0,M\) mapping.
- By using a compression function, the original data is transformed into a fixed-size hash value that can be used as an index to retrieve the original data from the data structure.
- The compression function also helps to ensure that the hash function produces uniformly distributed hash values. A good compression function should distribute the hash values evenly across the entire range of possible hash values, minimizing the risk of collisions where two different inputs produce the same hash value.

===========> If a compression function is not there :
Let's say we're mapping string --> int(32) without a mapping function.
Now, for having an int(32) output array, we will require (2^32)\*4 bytes which makes it 16GB of space.
Now, array is also a contiguous memory, so we will require 16 GB of contiguous RAM storage just to hold this data in a hashmap, which is very memory intensive. Thus compression function is mandatory.

Application Key --> Hash Key (Conversion done by HASHING FUNCTION)
Hash Key --> Smaller Domain (Conversion done by COMPRESSION FUNCTION)

<h2>CONFLICTS ARE INEVITABLE</h2>
Since the Keys are infinite and Hash Table array locations are finite, conflicts will be there for sure.
Thus, we have two collision resolution techniques to handle these conflicts :
1. Chaining
2. Open Addressing

<h3>1 - Chaining</h3>

In chaining, each bucket in the hash table contains a linked list of key-value pairs that have the same hash value. When a collision occurs (i.e., when two keys hash to the same bucket), the new key-value pair is added to the linked list at the corresponding bucket.

When retrieving a value associated with a particular key, the hash function is used to compute the hash value of the key, and then the linked list at the corresponding bucket is traversed until the key is found or the end of the list is reached.

Here, in the above case, the worst case time complexities are:
Insertion : O(1) since we add the {Key,Value} at the Head of Linked List only.
Search : O(N) where N is the number of elements inserted in the Hash Table (when all of them have the same hash value).
Deletion : O(N) as above.

In case of Average Case Time Complexity for search and deletion, 
=====>>>
Let's suppose the size of hashtable is M and the number of elements inserted in the the hashtable is N.
Now, assuming that the elements inserted are distributed uniformly across the table, we have:
alpha = N/M ;
Thus, the average case time complexity is O(1+alpha).

![[WhatsApp Image 2023-05-04 at 05.30.39.jpg]]

However, to improve the Time Complexity, we can use some other data structure instead of Linked List (Eg: Self Balancing BST) when we are expecting large number of collisions.
Here, Insertions are not O(1) but lookups are O(h).

![[WhatsApp Image 2023-05-04 at 05.30.40.jpg]]

<h2> 2 - Open Addressing </h2>
Open addressing is a collision resolution technique used in hash tables, which are data structures that store key-value pairs and use hash functions to index the keys.

In open addressing, when a collision occurs (i.e., when two keys hash to the same bucket), a new location is found within the hash table to store the key-value pair, instead of adding it to a linked list as in chaining. This is achieved by probing the hash table using a sequence of hash values derived from the original hash value of the key until an empty slot is found.

Methods of generating probe sequences:
<h3> A - Linear Probing </h3>
