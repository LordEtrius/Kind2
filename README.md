Kind2
=====

**Kind2** is is a **functional programming language** and **proof assistant** that is **lazy**,
**non-garbage-collected** and **massively parallel**. 

It is entirely based on [HVM](https://github.com/kindelia/hvm), a massively parallel runtime, making it astonishingly
fast. Its type-checker outperforms every other proof assistant on the market, and its runtime competes with Haskell's
GHC, often offering significant speedups. In short, Kind2 is as high-level as [Haskell](https://www.haskell.org/), as
memory efficient as [Rust](https://www.rust-lang.org/), and as strongly-typed as
[Agda](https://wiki.portal.chalmers.se/agda/pmwiki.php)'s, and it aims to become the ultimate programming language of
the next century. For direct comparisons, check our [functional
benchmarks](https://github.com/kindelia/functional-benchmarks) repository.

**Welcome to the inevitable parallel, functional future of computers!**

Examples
--------

Pure functions are defined via equations, as in [Haskell](https://www.haskell.org/):

```javascript
// Applies a function to every element of a list
map <a> <b> (list: List a) (f: a -> b) : List b
map a b Nil              f = Nil
map a b (Cons head tail) f = Cons (f x) (map tail f)
```

Side-effective programs are written via monadic monads, resembling [Rust](https://www.rust-lang.org/) and [TypeScript](https://www.typescriptlang.org/):

```javascript
// Prints the double of every numbet up to a limit
Main : IO (Result () String) {
  ask limit = IO.prompt "Enter limit:"
  for x in (List.range limit) {
    IO.print "{} * 2 = {}" x (Nat.double x)
  }
  return Ok ()
}
```

Theorems can be proved inductivelly, as in [Agda](https://wiki.portal.chalmers.se/agda/pmwiki.php) and [Idris](https://www.idris-lang.org/):

```idris
// Black Friday Theorem. Proof that, for every Nat n: n * 2 / 2 == n.
Nat.black_friday_theorem (n: Nat) : Equal Nat (Nat.half (Nat.double n)) n
Nat.black_friday_theorem Nat.zero     = Equal.refl
Nat.black_friday_theorem (Nat.succ n) = Equal.apply (x => Nat.succ x) (Nat.black_friday_theorem n)
```

For more examples, check the [Wikind](https://github.com/kindelia/wikind).

Installation
------------

Install [Rust](https://www.rust-lang.org/tools/install) first, then enter:

```
cargo install kind2
```

Enter `kind2` on the terminal to make sure it worked.

Usage
-----

Command    | Usage                     | Note
---------- | ------------------------- | --------------------------------------------------------------
Check      | `kind2 check  file.kind2` | Checks all definitions.
Eval       | `kind2 eval   file.kind2` | Runs using the type-checker's evaluator.
Run        | `kind2 run    file.kind2` | Runs using HVM's evaluator, on Rust-mode.
To-HVM     | `kind2 to-hvm file.kind2` | Generates a [.hvm](https://github.com/kindelia/hvm) file. Can then be compiled to C.
To-KDL     | `kind2 to-kdl file.kind2` | Generates a [.kdl](https://github.com/kindelia/kindelia) file. Can then be deployed to [Kindelia](https://github.com/kindelia/kindelia).
