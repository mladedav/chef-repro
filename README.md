```
$ cargo chef --version
cargo-chef-chef 0.1.61
$ cargo chef prepare
$ cargo chef cook
WARNING stdout appears to be a terminal.
cargo-chef is not meant to be run in an interactive environment and will overwrite some existing files (namely any `lib.rs`, `main.rs` and `Cargo.toml` it finds).

To continue anyway, type `yes`: yes
    Updating crates.io index
error: failed to select a version for the requirement `log = "^0.0.1"` (locked to 0.0.1)
candidate versions found which didn't match: 0.4.19, 0.4.18, 0.4.17, ...
location searched: crates.io index
required by package `binary v0.0.1 (C:\Users\david\Documents\Personal\rust\chef-repro\binary)`
perhaps a crate was updated and forgotten to be re-vendored?
thread 'main' panicked at 'Exited with status code: 101', [...]\.cargo\registry\src\index.crates.io-6f17d22bba15001f\cargo-chef-0.1.61\src\recipe.rs:189:27
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
```

`Cargo.lock` before running the commands:
```
# This file is automatically @generated by Cargo.
# It is not intended for manual editing.
version = 3

[[package]]
name = "binary"
version = "0.1.0"
dependencies = [
 "log 0.4.19",
 "log 1.0.0",
]

[[package]]
name = "log"
version = "0.4.19"
source = "registry+https://github.com/rust-lang/crates.io-index"
checksum = "b06a4cde4c0f271a446782e3eff8de789548ce57dbc8eca9292c27f4a42004b4"

[[package]]
name = "log"
version = "1.0.0"
```

`Cargo.lock` after running the commands:
```
version = 3

[[package]]
name = "binary"
version = "0.0.1"
dependencies = ["log 0.4.19", "log 1.0.0"]

[[package]]
name = "log"
version = "0.0.1"
source = "registry+https://github.com/rust-lang/crates.io-index"
checksum = "b06a4cde4c0f271a446782e3eff8de789548ce57dbc8eca9292c27f4a42004b4"

[[package]]
name = "log"
version = "0.0.1"
```
