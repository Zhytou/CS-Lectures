# Index Concurrency Control

A concurrency control protocol is the method that the DBMS uses to ensure "correct" results for concurrent operations on a shared object.

## Latches Overview

### Locks vs. Latches

In database world, locks protects the database's logical contents from other transcations.

On the other hand, latches protects the critical sections of the DBMS's internal data structure from other threads.

   -      | Locks              | Latches
----------|--------------------|--------
separate..|User transcations   |Threads
protect...|Database contents   |Critical sections
mode......|Shared,Exclusive....|Read,Write

### Latch Mode

+ Read  mode:shared
+ Write mode:exclusive

### Latch Implementation

#### Blocking OS Mutex

+ Example:`std::mutex`

#### Test-and-Set Spin Latch(TAS)

+ Example:`std::atomic<T>`

#### Reader-Writer Latch

+ Allows for concurrent readers
+ Must manage read/write queues to avoid starvation
+ Can be implemented on top of spinlocks

## Hash Table Latching

Easy to support concurrent access due to the limited ways threads access the data structure:

+ All threads move in the same direction and only access a single page/slot at a time
+ Therefore, deadlocks are not possible.

### Page Latches

Each page has its own reader-write latch that protects its entire contents.

### Slot Latches

Each slot has its own latch.

## B+ Tree Latching

### Latch Crabbing/Coupling

Protocol to allow multiple threads to access/modify B+ tree at the same time. The basic idea includes:

+ Get latch for parent
+ Get latch for child
+ Release latch for parent if "safe"

A safe node is one that will not split or merge when updated.

+ Not full(on insertion)
+ More than half-full(on deletion)

### Better Latching Algorithm

Assume that the leaf node is safe.

Use read latches and crabbing to reach the target node and then verify that it is safe.

If the leaf node is not safe, then do previous algorithm using write latches.

## Leaf Node Scans

Latches do not support deadlock detection or avoidance.

The leaf node sibling latch acquisition protocol must support a "no-wait" mode.

## Delayed Parent Updates

When a leaf node overflows, delay updating its parent node.
