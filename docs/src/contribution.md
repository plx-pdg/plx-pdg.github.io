# Contribution guide

**WARNING: we are not open to contribution right now, this guide will be useful in the future or just for the PDG team.**

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

### Unit tests
TODO: when we know how to write them

### Integration tests
TODO: when we know how to write them

### UI testing
TODO: when we know how to write them

## CI/CD strategy
Most of the release process should be automated, this is why we configured GitHub actions to run different jobs.

### PR validation strategy
1. On each PR (and when new commits arrive) and on push on main, `cargo build` and `cargo test` are run to make sure everything is working
1. On each git tag, we will run a CI job to test, build and run `cargo publish` to release PLX on [crates.io](https://crates.io/crates/plx)

todo: document release process
todo: document other OS

### Release strategy

To release a new version of PLX, here are the manual steps:
1. Create a new release branch
1. Choose a new version number based following semantic version
1. Modify the `CHANGELOG.md` to document changes since last release
1. Modify the `Cargo.toml` with the chosen version
1. Run `cargo build` to update the duplicated version number in `Cargo.lock`
1. Push the changes
1. Open and merge PR of this release branch (tests must pass so we cannot release code with compilation errors)

The CI release job starts and detect a version change (version in `Cargo.toml` different from the latest git tag) so the release process start
1. Create a new tag with the extracted version
1. Create a new release on Github with a link to the `CHANGELOG.md`
1. Run `cargo publish` to publish plx on `crates.io`

The result is that running `cargo install plx` again will install the new version!
