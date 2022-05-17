# Common Collections

## Storing Lists of Values with Vectors

### Creating a New Vector

``` rust
let v : Vec<i32> = Vec::new();
let v = vec![1, 2, 3];
```

### Updating a Vector

``` rust
let mut v : Vec<i32> = Vec::new();
v.push(5);
v.push(6);
```

### Dropping a Vector Drops Its Elements

Like any other struct, a vector is freed when it goes out of scope. When the vector gets dropped, all of its contents are also dropped, meaning those integers it holds will be cleaned up. 

### Reading Elements of Vectors

There are two ways to reference a value stored in a vector: via indexing or using the get method. 

``` rust
fn main() {
    let v = vec![1, 2, 3, 4, 5];

    let third: &i32 = &v[2];
    println!("The third element is {}", third);

    match v.get(2) {
        Some(third) => println!("The third element is {}", third),
        None => println!("There is no third element."),
    }
}
```

Attempting to add an element to a vector while holding a reference to an item causes a error.

``` rust
fn main() {
    let mut v = vec![1, 2, 3, 4, 5];

    let first = &v[0];

    v.push(6);

    println!("The first element is: {}", first);
}

```

This error is due to the way vectors work: because vectors put the values next to each other in memory, adding a new element onto the end of the vector might require allocating new memory and copying the old elements to the new space, if there isn’t enough room to put all the elements next to each other where the vector is currently stored. In that case, the reference to the first element would be pointing to deallocated memory. The borrowing rules prevent programs from ending up in that situation.

### Iterating over the Values in a Vector

``` rust
fn main() {
    let v = vec![100, 32, 57];
    for i in &v {
        println!("{}", i);
    }
}
```

``` rust
fn main() {
    let mut v = vec![100, 32, 57];
    for i in &mut v {
        *i += 50;
    }
}
```