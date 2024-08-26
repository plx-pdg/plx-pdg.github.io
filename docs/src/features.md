# Features

We described a lot of details about the a better experience, problems of the current experience, but here is **a complete central list of features we need to develop** during PDG and some other ideas for later. Some of them will have a dedicated issue on GitHub, but this is easier to see the global picture and progress here.

## For PDG
### Functionnal requirements
| Feature | Status | Description |
| ------------- | -------------- | -------------- |
| View the Home page | TODO | |
| View the List page | TODO | With the list of skills and exos |
| C++ exo build+execution, but without configuration and without build folder visible | TODO | Support compiling C++ in single or multi files via Xmake without config in a separated build directory |
| Java exo build+execution, but without configuration and without build folder visible | TODO | Support compiling Java in single or multi files with `javac` |
| Exo creation with one main file or possibly more starting files | TODO | Support a way to describe those metadata and indicate which files are relevant. |
| Definition of automated check verifying outputs | TODO | |
| Run automated output checks on starting files | TODO | Run check, generate result and diff if it differs |
| Run automated output checks on solution files | TODO | Adapt the compilation to build the solution files instead, and do the same things, after having checked the base files. |
| Run | TODO | |
| | TODO | |
| | TODO | |
| | TODO | |

TODO: continue this list

### Non functionnal requirements
1. It should be easy to create new exos and maintain them, converting an existing C++ exo should take less than 2 minutes.
1. The watcher should be performant: it should only watch files that could be modified by the student or teacher, it should take less than 100ms to see detect a change.
1. PLX should be usable during exo creation too to make sure the checks are passing on
1. Once an exo is opened, with one IDE window at right and the terminal with PLX at left, the students should not need to open or move other windows and should be able to only `Alt+Tab`. All the automable steps should be automated to focus on learning tasks (including build, build configuration, running, output diffing, manual entries in terminal, detecting when to run, showing solution, switching to next exo).
1. Switching to next exo should take less than 10 seconds. After this time: the IDE should be opened with the new file, and PLX should show the new exo details.
1. Trivial exo files shoud not need any build configuration, PLX should be able to guess how to build the target with available files.

## For later
PDG is only 3 weeks but we already had some improvements or ideas for future development
| Feature | Status | Description |
| ------------- | -------------- | -------------- |
| Review mode | TODO | A big feature to help clone all forks, pull them regularly, run all tests, review specific exos, flag some answers. |
| A global progress grid | TODO | To easily view general progress in colors |
| "Lab/Single exo" mode | TODO | Just run a single exo definition without all the general project definition and lists around. |
| Concurrent execution of checks | TODO | If a CLI has 10 checks and it takes 2 seconds to execute, running all tests one after the other will take 20 seconds ! If we could run them in 2.1 seconds that would be much better !!|
| Smart execution of tests | TODO | Execute first failed displayed check first, then continue with next failing tests, and finally with already passing tests. Invent other strategies to run them more efficiently.|
| | TODO | |
| | TODO | |
| | TODO | |
| | TODO | |
| | TODO | |

