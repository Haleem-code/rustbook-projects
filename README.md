# What I learnt in the guessing game

A very small Rust command-line program that picks a secret number and asks the user to guess it.



- The program prints a prompt and reads a line from standard input.
- It converts the typed string into a number and compares it with a randomly generated secret number.
- The loop repeats until the user guesses correctly.

Key parts and what I learnt:

- `use std::io;`:brings input/output tools into scope so we can read what the user types.
- `use rand::Rng;`:imports the trait that lets us call `gen_range` to generate random numbers.
- `rand::thread_rng().gen_range(1..=100)`: creates a random number generator local to the current thread and generates an integer between 1 and 100 (inclusive).
- `String::new()` / `io::stdin().read_line(&mut guess)`:build a new string and read a line from the terminal into it.
- `guess.trim().parse()`:trims whitespace and tries to parse the string into a number; we handle parse errors with a `match` and `continue` to ask again.
- `cmp(&secret_number)` and `std::cmp::Ordering`:compares the guessed number and the secret number and tells the user `Too small!`, `Too big!`, or `You win!`.

Why `rand` is needed:

- The `rand` crate gives us functions to produce random numbers.
- The standard library does not include a simple, secure random number generator for these tasks, so we use `rand` to get different secret numbers each run.

How to run:

```
cargo run
```




