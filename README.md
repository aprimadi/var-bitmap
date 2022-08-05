# Var Bitmap

A simple variable-sized bitmap.

## Motivation

Most of the bitmap implementation I found on crates.io are either fixed-size
or compressed which isn't what I needed for my project. I want a growable 
bitmap that is expected to remain small. A compressed bitmap adds a lot of 
additional data structures on top of the bitmap itself which works great for 
large bitmap but adds a lot of unnecessary complexity for bitmap that is 
expected to remain small.

## Usage

```rust
use var_bitmap::Bitmap;

let bm = Bitmap::new();
bm.push(false);
bm.push(true);
bm.push(false);
bm.get(2); // Should be false
bm.set(2, true);
bm.get(2); // Should be true
```
