# Installation instructions

## Installation for development
### Environment

1. Install the Rust toolchain via `rustup` on [rustup.rs](https://rustup.rs/)
1. Install xmake on [xmake.io](https://xmake.io/#/guide/installation)
1. Clone the repository `git clone git@github.com:plx-pdg/plx.git`
1. We need to define how exos files are edited, for this we choose the standard `$EDITOR` environment variable
  1. You can choose any command line editor like `nano, vim, nvim` or others, but GUI IDE also works `code, codium, idea`, as a replacement of `<ide>` below.
  1. On Mac and Linux you should change your shell configuration (`~/.bashrc` for ex.) with a line like `export EDITOR=<ide>`
  1. On Windows `setx /m EDITOR <ide>` (check it worked you can run `echo %EDITOR%` in a new terminal)
  1. In case it doesn't work, make sure to reload your shell
  1. When you enter an exo your $EDITOR will automatically open the correct file

### Build
```sh 
cargo build
# or in release mode
cargo build --release
```

You can find the result binary in `target/debug/plx` and `target/release/plx`.

### Run
To run the binary without knowning its path just run `cargo run`.

## Production usage
We do not provide binaries for the project so you have to compile it yourself but it is easy via cargo.

1. Install the Rust toolchain via `rustup` on [rustup.rs](https://rustup.rs/)
1. Install xmake on [xmake.io](https://xmake.io/#/guide/installation)

To install PLX without cloning the repository, you can install and compile it from `crates.io` with

```sh
cargo install plx
```

And then just run the `plx` command in your terminal. (If it is not found make sure you restart your terminal or check if `~/.cargo/bin/` is in your $PATH).
