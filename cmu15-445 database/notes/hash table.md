# HASH TABLE

A hash table implements an associative array abstract data type that maps keys to values. It provides on average O (1) operation complexity and O (n) storage complexity.

A hash table implementation is comprised of two parts:

+ **Hash fucntion**: How to map a kep into a domain. This is used to compute an index into an array of buckets or slots.
+ **Hash scheme**: How to handle key collisions after hashing.

## NON-NNIQUE KEYS

### SEPARATE LINKED LIST

Store values in separate storage area for each key.

### REDUNDANT KEYS

Store duplicate key entries together in the hash table.

## STATIC HASHING SCHEMES

### LINEAR PROBE HASHING

+ Resolve collisions by linearly searching for the next free slot in the table
+ To see if value is present, go to slot using hash, and scan for the key. The scan stops if you find the desired key or you encounter an empty slot.

### ROBIN HOOD HASHING

+ Each key tracks the number of positions they are from where its optimal position in the table.
+ On insert, a key takes the slot of another key if the first key is farther away from its optimal position
than the second key. The removed key then has to be re-inserted back into the table.

### CUCKOO HASHING

+ On insert, check every table and pick anyone that has a free slot.
+ If no table has free slot, evict element from one of them, and rehash it to find a new location.
+ If we find a cycle, then we can rebuild all of the hash tables with new hash function seeds (less
common) or rebuild the hash tables using larger tables (more common).

## DYNAMIC HASHING SCHEMES

### CHAINED HASHING

+ Resolves collisions by placing elements with same hash key into the same bucket.
+ If bucket is full, add another bucket to that chain. The hash table can grow infinitely because the
DBMS keeps adding new buckets.

### EXTENDIBLE HASHING

+ The DBMS maintains a global and local depth bit counts that determine the number bits needed to find buckets in the slot array.
+ When a bucket is full, the DBMS splits the bucket and reshuffle its elements. If the local depth of the split bucket is less than the global depth, then the new bucket is just added to the existing slot array. Otherwise, the DBMS doubles the size of the slot array to accommodate the new bucket and increments the global depth counter.

### LINEAR HASHING

+ When any bucket overflows, split the bucket at the pointer location by adding a new slot entry, and create a new hash function.
+ If hash function maps to slot that has previously been pointed to by pointer, apply the new hash function.
+ When pointer reaches last slot, delete original hash function and replace it with new hash function.