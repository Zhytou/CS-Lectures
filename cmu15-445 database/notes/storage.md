# DATABASE STORAGE

> Database is a bunch of layers built on top pf each other. From the bottom to the top, the layer is disk manager, buffer pool manager, access method, operation excution and query planning.

## DISK-ORIENTED ARCHITECTURE

The course focuses on disk-oriented DBMS, which means that the primary storage location of the database is on non-volatile disk.

### STORAGE HIERARCHY

CPU Register, CPU Cache

Memory(DRAM)

Disk(SSD, HDD, Network Storage)

#### VOLTATILE DEVICES

+ Volatile means that if you pull the power from the machine, then the data is lost.
+ Volatile storage supports fast random access with byte-addressable locations. This means that the program can jump to any byte address and get the data that is there.
+ For our purposes, we will always refer to this storage class as “memory.”

#### NON-VOLTATILE DEVICES

+ Non-volatile means that the storage device does not need to be provided continuous power in order for the device to retain the bits that it is storing.
+ It is also block/page addressable. This means that in order to read a value at a particular offset, the program first has to load the 4 KB page into memory that holds the value the program wants to read.
+ Non-volatile storage is traditionally better at sequential access (reading multiple contiguous chunks of data at the same time).
+ We will refer to this as “disk.” We will not make a (major) distinction between solid-state storage(SSD) and spinning hard drives (HDD).

### THE PROCESS OF GETTING A PAGE IN DBMS

+ Execution Engine ask Buffer Pool for xx page
+ Buffer Pool load Page Directory from the Disk and find xx page
+ Buffer Pool load xx pgae from the Disk and then handle it to the Execution Engine

It is pretty the same as the OS reading a page, so why does the DBMS need a disk manager layer, why not use OS?

### WHY NOT USE THE OS?

Because the correctness.

DBMS (almost) always wants to control thingsitself and can do a better job at it.

## HOW THE DBMS REPRESENTS THE DATABASE IN FILES ON DISK?

### FILE STORAGE

#### STORAGE MANAGER

The storage manager is responsible for maintaining a database's files.It organizes the files as a collection of pages.

#### DATABASE PAGES

A page is fixed-size block of data. Each page is given a unique identifier.

There are three different notions of "pages" in a DBMS:

+ Hardware Page(4K)
  + By Hardware page, we mean at what level the device can guarantee a "failsafe" write.
+ OS Page(4K)
+ Database Page(512B-16KB)

#### DATABASE HEAP FILE ORGANAZATION

Page diretctory is a special page that the DBMS maitains to track the location of data pages in the database files.

### PAGE LAYOUT

Every page contains a header of metadata about the page's contents.

+ page size
+ checksum
+ DBMS version
+ ...

#### SLOTTED PAGE

Slotted Pages: Page maps slots to offsets.

+ Header keeps track of the number of used slots, the offset of the starting location of the last used slot, and a slot array, which keeps track of the location of the start of each tuple.
+ To add a tuple, the slot array will grow from the beginning to the end, and the data of the tuples will grow from end to the beginning. The page is considered full when the slot array and the tuple data meet.

#### LOG-STRUCTURED FILE ORGANIZATION

Instead of storing tuples in pages, the DBMS only stores log records about how the database was modified.

Comparing to the slotted page orgnization, this way make the best use of better performance on sequential read/write than random read/write.

### TUPLE LAYOUT

### DATA REPRESPENTATION

### SYSTEM CATALOGS

### STORAGE MODEL

## HOW THE DBMS MANAGES ITS MEMORY AND MOVE DATA BACK-AND-FORTH FROM DISK?

> it is covered in buffer pool.md.