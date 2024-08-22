# Contribution guide

## Development

In addition to have installed the prerequisites in the Installation page, you have to
1. Clone the repository `git clone git@github.com:plx-pdg/plx.git`
1. Go into the `plx` folder
1. Build the program 
    ```sh 
    cargo build
    # or in release mode
    cargo build --release
    ```
    You can find the result binary respectively in `target/debug/plx` and `target/release/plx`.
1. And/or run it
    To run the binary without knowning its path just run `cargo run`.

## Tips
1. Install crate `cargo-watch` (`cargo install cargo-watch`) and run `cargo watch -x run -c` to rebuild and run `cargo run` and clear the screen between each execution. This provides a very convenient feedback loop.

## Writing tests

TODO: when we know how to write them
