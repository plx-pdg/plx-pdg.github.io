### why rust ?

Rust was chosen for our program for several key reasons : 

1. **Performance**: Rust is renowned for its high performance, comparable to languages like C and C++. This is crucial for our application, where speed and efficiency are paramount. 2. Memory safety: Rust's ownership model ensures memory safety. This reduces the chances of memory leaks and other related bugs making the application more robust.
2. **Memory Safety**: One of Rust’s standout features is its ownership model, which enforces strict memory safety at compile time 
2. **Concurrency**: Rust's concurrency allows us to write safe concurrent code. This is particularly important for our application, as many modules within PLX require multithreading. Rust's concurrency model ensures that interactions between these modules are safe and efficient, leading to better performance and stability.Many moduls of PLX need threads and therefore we need to ensure that the concurrency in between those moduls are safe.
3. **Crates**: Rust’s ecosystem is enriched by a vast collection of libraries, known as crates, which provide pre-built functionalities for various tasks. 

### why ratatui ?

Ratatui provides a simple and intuitive API for building TUIs, which speeds up the developpement process. User side, it provides an ease of use rather than using terminal commands. Ratatui is also very flexible and offers a high degree of flexibility in designing widgets and layouts allowing us to create a clean, simple, and easy to use user interface that meets our specific needs.

Our TUI also needs to remain responsive. Ratatui is designed to be performant.

### why a TUI

TUIs are inherently lightweight and consume fewer system resources compared to GUIs. his makes them particularly suitable for environments with limited resources or where performance is a critical concern.

TUIs often rely on keyboard shortcuts and command-line inputs, which can be much faster for experienced users to navigate than using a mouse with a GUI. This can lead to increased productivity and a more streamlined workflow. In our case, PLX is made for practising and exercising programming language and therefore need to stay in an coding environnement and not a GUI.

