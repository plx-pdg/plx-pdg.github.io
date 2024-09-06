# Development documentation

TODO: insert TOC here

## Introduction
The goal of this documentation is to make sure important decisions and non obvious information that is useful to new and existing contributors is documented. This is important is to make the project future-proof and maintainable.  
If you want to make a non trivial contribution to the project, you really should read it most or some of the useful sections related to your problem, in addition to having a global overview of the features implemented. Knowing each module goal at least is important so you can see the different pieces fitting together.


TODO: write this at the end of PDG time once we have a good structure

## Current architecture
TODO: add date
TODO: add new schema
TODO: explain the events system + async advantages + 

## Modules goals and useful details

### Test suite
TODO: dump test suite pretty output here

### UI
A Ratatui based UI that is as dumb as possible because this is the hardest part to test. Most of the code should be just definition of UI components. The UI read the `core.ui_state` enum to know which page and situation to display and renders the appropriate page at the rate of TODO.

1. Keyboard shortcuts are just sent as event to the core, nothing is done with them directly. 
TODO: Exception of Q ?

TODO: Testing ?

### Parser
TODO: Testing ?

The Parser collectively provide functionality for serializing and deserializing data to and from toml's files format. TIt convert TOML strings into Rust data structures and vice versa using the serde library. These functions handle the conversion by leveraging serde's DeserializeOwned and Serialize traits, ensuring that any compatible Rust type can be easily transformed to and from TOML format. This allows for efficient data interchange and configuration management in applications that use TOML for configuration files.


### Compiler
TODO: Testing ?


### Runner
TODO: Testing ?

### Watcher
TODO: Testing ?

The FileWatcher is designed to monitor a specified directory for file modifications. It runs in a separate thread and uses channels to communicate events back to the main thread. The provided tests, verify its functionality by checking if the watcher correctly detects changes in both nested folders and the root of the watched directory. When a file is modified, the watcher sends an event through the channel, which the test then asserts to ensure the correct event (Event::FileSaved) is received.

## Encountered issues
1. Colors not visible in CI after using `console` crate: the test in CI run in a non interactive process (you can simulate this by running `cargo test > output`), so the colors were not applied so we couldn't compare it with expected "ANSI codes included output".
    ```rust
    // from diff.rs
    console::set_colors_enabled(true); // this is how we can force colors
    let old = "Hello\nWorld\n";
    let new = "Hello\nWorld Test\n";
    let diff = Diff::calculate_difference(old, new, None);
    let ansi = diff.to_ansi_colors(); // this is where the console create is called
    let expected_ansi = r"[2m [0m[2mHello
    [0m[31m[1m-[0m[31m[1m[2mWorld[0m[31m[1m[2m
    [0m[32m[1m+[0m[32m[1m[2mWorld[0m[32m[1m Test[0m[32m[1m[2m
    [0m";
    ```

## Tips for testing
1. Better debug in test output
    1. Debug view and pretty printing: `println!("{:#?}", exo);` and `exo` must have the `Debug` trait implemented, the easiest way to do it is with.
    1. Printing colors `println!("{}", diff.to_ansi_colors());` via `cargo test -- nocapture` to not hide `println` during tests.


## Logo design

In the spirit of Delibay and PRJS logos, a simple gradient was chosen on the project name. Like PRJS, the text is an ASCII art creation. It was generated with the help of [Calligraphy](https://calligraphy.geopjr.dev/) with the font `Blocky`. The gradient is composed of these 2 colors: `#fc1100`, `#ffb000` applied to this text piece.

```
████████  ██       ██     ██ 
██     ██ ██        ██   ██  
██     ██ ██         ██ ██   
████████  ██          ███    
██        ██         ██ ██   
██        ██        ██   ██  
██        ████████ ██     ██ 
```

It was colored in Inkscape with a monospace font (any monospace font should be okay) and exported in SVG:

![logo of PLX](../../static/logo.svg)
