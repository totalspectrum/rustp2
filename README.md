# rustp2

Rust for Parallax P2 (using RISC-V translation based on riscvp2)

This is a project for running programs compiled with the Rust programming language on the Parallax Propeller 2 (P2).

It works on the same principle as the riscvp2 C compiler for the P2 (https://github.com/totalspectrum/riscvp2), namely it uses a custom linker script to add a RISC-V to P2 JIT compiler to a RISC-V executable built with the standard Rust toolchain.

## Setting up Rust

On your host PC (I used Linux Debian 12, other OSes may vary), make sure you have rust already installed via rustup. For doing that, see https://www.rust-lang.org/tools/install

Now add support for riscv32-imac:

```
rustup default stable
rustup target add riscv32-imacunknown-none-elf
cargo install cargo-binutils
```

## Building for P2

Make sure the submodules are up to date:
```
git submodule update --init --recursive
```

Then go into riscvp2-rt and build:
```
cd riscvp2-rt
cargo build
```

And finally the test app that blinks an LED on your P2:
```
cd ../riscvp2-testapp
cargo run
```
