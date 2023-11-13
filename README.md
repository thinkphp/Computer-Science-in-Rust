# RUST Language
  
  RUST is a systems programming language that runs blazingly fast, prevents
  segfaults, and guarantees thread safety.

```
$ rustc hello.rs

fn main() {
    // Statements here are executed when the compiled binary is called.
    
    //println! is a macro that prints text to the console.
    println!("Hello World!");
}
```  

## Scalar Types

* Signed integers: i8, i16, i32, i64, i128 and isize (pointer size)
* Unsigned integers: u8, u16, u32, u64, u128 and usize (pointer size)
* Floating point: f32, f64
* char Unicode scalar values like 'a', 'α' and '∞' (4 bytes each)
* bool either true or false
* The unit type (), whose only possible value is an empty tuple: ()
* Despite the value of a unit type being a tuple, it is not considered a compound type because it does not contain multiple values.

### Featuring

    * pattern matching
    * efficient C bindings
    * type inference
    * minimal runtime
