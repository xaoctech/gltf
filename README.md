
<h1 align="center">
    gltf
</h1>
<p align="center">
   <a href="https://travis-ci.org/alteous/gltf">
      <img src="https://travis-ci.org/alteous/gltf.svg?branch=master" alt="travis">
   </a>
   <a href="https://crates.io/crates/gltf">
      <img src="https://img.shields.io/crates/v/gltf.svg" alt="crates.io">
   </a>
   <a href="https://docs.rs/gltf">
      <img src="https://docs.rs/gltf/badge.svg" alt="docs.rs">
   </a>
   <a href="https://gitter.im/alteous/gltf">
      <img src="https://img.shields.io/gitter/room/alteous/gltf.svg" alt="gitter">
   </a>
</p>
<hr>

This crate is intended to load [glTF 2.0](https://www.khronos.org/gltf), a file format designed for the efficient transmission of 3D assets.

`rustc` version 1.15 or above is required.

### Usage

#### Import some glTF 2.0

```rust
extern crate gltf;

fn main() {
    let path = std::env::args().nth(1).unwrap();
    match gltf::import::from_path_sync(&path) {
        Ok(gltf) => println!("{:#?}", gltf),
        Err(err) => println!("Invalid glTF ({:?})", err),
    }
}
```

### Extras and Names

By default, `gltf` ignores all `extras` and `names` included with glTF assets. You can negate this by enabling the `extras` and `names` features, respectively.

```toml
[dependencies]
gltf = { version = "0.6", features = ["extras"] }
```

### Examples

#### gltf-display

If you want to see how the structure of the glTF file is deserialized, you can
use the example here to poke at it.

```sh
cargo run --example gltf-display glTF-Sample-Models/2.0/Box/glTF/Box.gltf
```

