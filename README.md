# Essential Rust.

Rust is a programming language that helps you write faster, more reliable software. High-level ergonomics and low-level control are often at odds with each other in programming language design; Rust stands to challenge that. Through balancing powerful technical capacity and a great developer experience, Rust gives you the option to control low-level details (such as memory usage) without all the hassle traditionally associated with such control.

```
extern crate rand;

use std::io;
use std::cmp::Ordering;
use rand::Rng;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1, 101);

    println!("The secret number is: {}", secret_number);

    println!("Please input your guess.");

    let mut guess = String::new();

    io::stdin().read_line(&mut guess)
        .expect("Failed to read line");

    let guess: u32 = guess.trim().parse()
        .expect("Please type a number!");

    println!("You guessed: {}", guess);

    match guess.cmp(&secret_number) {
        Ordering::Less => println!("Too small!"),
        Ordering::Greater => println!("Too big!"),
        Ordering::Equal => println!("You win!"),
    }
}
```  

### Featuring
    * pattern matching
    * efficient C bindings
    * type inference
    * minimal runtime  


```
$ rustc hello.rs
$ ./hello
Hello World!

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

## While Control Flow

```
fn main() {
    // A counter variable
    let mut n = 1;

    // Loop while `n` is less than 101
    while n < 101 {
        if n % 15 == 0 {
            println!("fizzbuzz");
        } else if n % 3 == 0 {
            println!("fizz");
        } else if n % 5 == 0 {
            println!("buzz");
        } else {
            println!("{}", n);
        }

        // Increment counter
        n += 1;
    }
}
```

## if/else Control Flow
```
fn main() {
    let n = 5;

    if n < 0 {
        print!("{} is negative", n);
    } else if n > 0 {
        print!("{} is positive", n);
    } else {
        print!("{} is zero", n);
    }

    let big_n =
        if n < 10 && n > -10 {
            println!(", and is a small number, increase ten-fold");

            // This expression returns an `i32`.
            10 * n
        } else {
            println!(", and is a big number, halve the number");

            // This expression must return an `i32` as well.
            n / 2
            // TODO ^ Try suppressing this expression with a semicolon.
        };
    //   ^ Don't forget to put a semicolon here! All `let` bindings need it.

    println!("{} -> {}", n, big_n);
}
```

 ## Euclid's Algorithm https://ideone.com/Yv1jcj

```
use std::io;
use std::str::FromStr;
use std::cmp::Ordering;

fn get_number(prompt_input: &str) -> u32 {

       println!("{}", prompt_input);
       
       let mut input = String::new();
       
       io::stdin().read_line(&mut input).expect("no input!");     
       
       u32::from_str(input.trim()).unwrap()      
}

fn main() {
     
       let a = get_number("Enter first number a = ");
       
       let b = get_number("Enter first number b = ");

       println!("The Greatest Common Divisor of {} and {} is {}", a, b, euclid( a, b) );       
}

fn euclid(a: u32, b: u32) -> u32 {
 
   assert!(a > 0 && b > 0);
   
   match a.cmp(&b) {
   
      Ordering::Equal => b,
      
      Ordering::Less => euclid(a,b-a),
      
      Ordering::Greater => euclid(a-b,b)
   }   
}
```

## References

* https://doc.rust-lang.org/stable/rust-by-example
* https://web.mit.edu/rust-lang_v1.25/arch/amd64_ubuntu1404/share/doc/rust/html/#the-rust-bookshelf
