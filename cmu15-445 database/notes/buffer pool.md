# BUFFER POOL

> How the DBMS manage its memory and move data back-and-forth from disk?

Spatial Control:

+ Where to write pages on disk.
+ The goal is to keep pages that are used together often as
physically close together as possible on disk.

Temporal Control:

+ When to read pages into memory, and when to write them to disk.
+ The goal is minimize the number of stalls from having to read data from disk.

## BUFFER POOL MANAGER

Page table keeps track of pages that are currently in memory.

## REPLACEMENT POLICY

## OTHER MEMORY POOLS
