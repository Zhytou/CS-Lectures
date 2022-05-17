# Common Concepets

## Variable

### Variables and Mutability

*Variables* are immutable only by default. You can make them mutable by adding `mut` in front of the variable name.

### Constants

Like immutable variables, *constants* are values that are bound to a name and are not allowed to change, but there are a few differences between constants and variables:

+ First, you aren't allowed to use `mut` with constants.
+ Second, you declare constants using the `const` keyword instead of the `let` keyword, and the type of the value must be annotated.
+ Third, constants can be declared in any scope, including the global scope.
+ Last, the constants may be set only to a constant expression, not the result of a value that could be only be computed at runtime.

Here's an example of a constant declaration:

``` rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

### Shadowing

You can declare a new variable with the same name as a previous variable. This is what we call *shadowing*, which means  means that the second variable’s value is what the program sees when the variable is used.

## Data Types

### Scalar Types

### Compound Types

## Functions

Rust code uses snake case as the conventional style for function and variable names, in which all letters are lowercase and underscores separate words.

### Statements and Expressions

Function bodies are made up of a series of statements optionally ending in an expression.

Statements are instructions that perform some action and do not return a value. Expressions evaluate to a resulting value.

Function definitions are also statements; the entire preceding example is a statement in itself.

## Comments

In Rust, the idiomatic comment style starts a comment with two slashes, and the comment continues until the end of the line.
