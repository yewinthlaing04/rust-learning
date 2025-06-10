Rust Fundamentals: Variables, Data Types, and Shadowing
This document outlines key concepts in Rust, including variable immutability, data types, and the concept of shadowing.

Variables and Immutability
In Rust, variables are immutable by default. This means that once a value is bound to a variable, it cannot be changed.

To make a variable mutable, you must explicitly use the mut keyword:

Rust

let mut var_a = 5; // var_a is mutable and can be reassigned
var_a = 6;         // This is allowed
If you try to reassign an immutable variable, you will get a compile-time error:

Rust

let var_b = 5; // var_b is immutable
// var_b = 6;  // This would result in a compile-time error
Constants
Constants in Rust are also immutable, but they differ from variables in a few ways:

They are declared using the const keyword instead of let.
You are not allowed to use mut with constants. Constants are always immutable.
The type of a constant must be annotated.
Constants can only be set to a constant expression, not the result of a function call or any other runtime value.
Example:

Rust

const MAX_POINTS: u32 = 100_000; // MAX_POINTS is a constant
// const mut MIN_POINTS: u32 = 10; // ERROR: cannot use `mut` with `const`
Shadowing
Shadowing is a feature in Rust where you can declare a new variable with the same name as a previous variable. The new variable "shadows" the old one, meaning that any subsequent code will refer to the new variable's value. The original variable still exists in memory but cannot be accessed.

Shadowing is different from marking a variable as mut. With mut, you are changing the value of the same variable. With shadowing, you are creating a new variable.

This is particularly useful when you want to transform a value but keep the same variable name.

Example of shadowing:

Rust

fn main() {
    let spaces = "   "; // First `spaces` variable (string slice)
    let spaces = spaces.len(); // Second `spaces` variable (usize, result of .len())

    println!("The number of spaces is: {}", spaces); // Prints: The number of spaces is: 3
}
Data Types
Rust is a statically typed language, meaning it must know the types of all variables at compile time.

Scalar Types
Scalar types represent a single value.

Integers: Whole numbers.

Signed integers (i8, i16, i32, i64, i128): Can store positive or negative numbers.
Unsigned integers (u8, u16, u32, u64, u128): Can only store positive numbers.
isize and usize: Pointer-sized integers. Their size depends on the architecture of the computer (e.g., 32 bits on a 32-bit architecture, 64 bits on a 64-bit architecture). They are often used for indexing collections.
Floating-Point Numbers: Numbers with decimal points.

f32: Single-precision float.
f64: Double-precision float (default in Rust).
Booleans: Represent truth values.

bool: Can be true or false.
Characters: Single Unicode scalar values.

char: Represented by single quotes (e.g., 'a', '😊').
Compound Types
Compound types can group multiple values into one type.

Tuples: Fixed-size ordered lists of values of different types.

Tuple elements can be accessed by destructuring or by using dot notation followed by the index.
Rust

fn main() {
    let tup: (i16, f32, u8) = (500, 6.4, 1);

    // Destructuring
    let (x, y, z) = tup;
    println!("The value of y is: {}", y); // Prints: The value of y is: 6.4

    // Accessing by index
    let five_hundred = tup.0;
    let six_point_four = tup.1;
    let one = tup.2;
}
Arrays: Fixed-size collections of elements of the same type. (Not explicitly mentioned in your input, but a common compound type).

Rust

// Example of an array (for completeness, not in your original input)
let a = [1, 2, 3, 4, 5];
let months = ["January", "February", "March", "April", "May", "June"];
