# Installation instructions

## Prerequisites

1. Install the Rust toolchain via `rustup` on [rustup.rs](https://rustup.rs/), so you have the package manager cargo and the necessary tools to compile plx from the `crates.io` package.

If you are programming in
1. C or C++: standard build tools for C/C++, used by Xmake
1. Configure `$EDITOR` environment variable to define your IDE. This way PLX can auto start your IDE
    1. Currently, we only support `code`, `codium`, `idea`. 
        1. For now this feature is unstable for terminal based editors. Feel free to create a new issue if you do not see your favorite IDE here.
    1. On Mac and Linux you should change your shell configuration (`~/.bashrc` for ex.) with a line like `export EDITOR=<ide>`
    1. On Windows `setx /m EDITOR <ide>` (check it worked you can run `echo %EDITOR%` in a new terminal)
    1. If it doesn't work, make sure to reload your shell
    1. When you enter an exo your `$EDITOR` will automatically open the correct file

## Installation for students and teachers
We do not provide binaries for the project so you have to compile it yourself but it is easy via cargo.

To install PLX without cloning the repository, you can install and compile it from `crates.io` with

```sh
cargo install plx
```

And then just run the `plx` command in your terminal. (If it is not found make sure you restart your terminal or check if `~/.cargo/bin/` is in your $PATH).

**Note: we might provide binaries later for ease of installation, it is not a priority right now.**
