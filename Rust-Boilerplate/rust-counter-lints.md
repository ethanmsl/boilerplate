

# Keep Clippy from telling you to force variables into strings.
A recent (time of writing) lint prefers `println!("{hiya:?}")` over `println!("{:?}", hiya)`  
While that makes sense in isolation and black & white:
 - (a) rust LSP and parser won't recognize the variable in the string and won't syntax color it, nor allow hover text
 - (b) not all variables can be ergonomically placed inside text, leading the lint to push for a kind of inconsistent style

```rust
// disable clippy lint prevent a lint from running
#![allow(clippy::uninlined_format_args)]
```
