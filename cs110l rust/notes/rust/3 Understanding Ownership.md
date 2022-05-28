# Understanding Ownership

Ownership is Rust’s most unique feature and has deep implications for the rest of the language. It enables Rust to make memory safety guarantees without needing a garbage collector, so it’s important to understand how ownership works.

## What Is Ownership?

*Ownership* is a set of rules that governs how a Rust program manages memory. All programs have to manage the way they use a computer’s memory while running. Java or Go have garbage collection that constantly looks for no-longer used memory as the program runs; in C++ or C, the programmer must explicitly allocate and free the memory. Rust uses a third approach: memory is managed through a system of ownership with a set of rules that the compiler checks. If any of the rules are violated, the program won’t compile. None of the features of ownership will slow down your program while it’s running.

### Ownership Rules

+ Each value in Rust has a variable that’s called its owner.
+ There can only be one owner at a time.
+ When the owner goes out of scope, the value will be dropped.

### Variable Scope

A *scope* is the range within a program for which an item is valid.

## References and Borrowing

A reference is like a pointer in that it’s an address we can follow to access data stored at that address that is owned by some other variable. Unlike a pointer, a reference is guaranteed to point to a valid value of a particular type.

You can borrow a value using reference instead of taking ownership of the value.

### Mutable References

Use a *mutable reference* to modify a borrowed value.
However, mutable references have one big restriction: you can have only one mutable reference to a particular piece of data at a time.

You can have several borrowing references or one mutable reference(the mutable variables should not be modified at same time) at one time.

### Dangling References

In Rust, the compiler guarantees that references will never be dangling references: if you have a reference to some data, the compiler will ensure that the data will not go out of scope before the reference to the data does.

## The Slice Type

Slices let you reference a contiguous sequence of elements in a collection rather than the whole collection. A slice is a kind of reference, so it does not have ownership.
