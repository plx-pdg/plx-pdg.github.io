# Exos management

This is a documentation driven design, this is the state of our research on the best exos management solution for the supported languages. This will probably be useful to future contributors who might want to understand why we made these decisions, help other `*lings` projects in their thinking,

## Defining all toml

### course.toml 
To create a course we need a name and a selection of skills (chapters) in a specific order.

### skill.toml
To create a new skill, we need a name and a list of all the names of each exercices in a specific order.

```toml
name = 'Introduction'
exos = ['basic-args', 'basic-output']
```

### Exo-state.toml
For each exercice, there is a state that can be in-progress, done or not done. There is also an optional favorite option to place the exercice into our personal selection.

```toml
state = "InProgress"
favorite = false
```

### exo.toml
For each exercice we have :
- a name
- the instructions
- all the needed checks to be done

```toml
name = 'Basic arguments usage'
instruction = 'The 2 first program arguments are the firstname and number of legs of a dog. Print a full sentence about the dog. Make sure there is at least 2 arguments, print an error if not.'
[[checks]]
name = 'Joe + 5 legs'
args = ["Joe", "5"]
test = {type= "output", expected = "The dog is Joe and has 5 legs" }
[[checks]]
name = 'No arg -> error'
test = {type= "output", expected = "Error: missing argument firstname and legs number"}
[[checks]]
name = 'One arg -> error'
args = ["Joe"]
test = {type = "output", expected = "Error: missing argument firstname and legs number"}
```

## Defining "the best"
We believe the best structure will lead to the following qualities: 
1. Speed to create new exos and editing existing ones
1. Ease of learning the structure and synatx to create and maintain exos
1. Ease of developing a solution and adding checks without always writing unit tests with test runner

This can be measured with the following speed metrics:
1. Converting an existing C++ exo should take less than 2 minutes.
1. Converting "here is the expected output" to a PLX check should take less than 15seconds

## Goal
1. Define a folder and file structure to define a single exo and an entire course with all exos grouped by skills (sometimes we could just call them chapters).
1. Define the syntax used to define the various exo metadata
1. Define build configuration files and build hints if necessary
1. Show different examples for various exo types in the 3 languages
1. Define templates used to quickly fill new exos and how to use them

## Research on similar tools
Existing projects like `rustlings` and inspired projects like `haskellings`, `cplings`, `ziglings`, and even PRJS has opinions on their structure and their metadata system. Each language have its own constraints, build system, ease of testing, and testing tools integration... but there is probably new ideas and things to inspire from these tools. In addition to reading the contributing guides, looking at GitHub issues from new contributors on these repositories could also indicate advantages or flaws in the structure that can help us decide which direction to take.

### Rustlings
Website: [rustlings.cool](https://rustlings.cool) - [CONTRIBUTING.md](https://github.com/rust-lang/rustlings/blob/main/CONTRIBUTING.md) - [Third party exos (outside of Rustlings repos)](https://github.com/rust-lang/rustlings/blob/main/THIRD_PARTY_EXERCISES.md) 


### PRJS

Website: [Repos samuelroland/prjs](https://github.com/samuelroland/prjs) - Exo management: [exos.md](https://github.com/samuelroland/prjs/blob/main/exos.md)

### Cplings
Website: [Repos rdjondo/cplings](https://github.com/rdjondo/cplings) - Exo management: [exos.md](https://github.com/samuelroland/prjs/blob/main/exos.md)

### Golings
Website: [Repos mauricioabreu/golings](https://github.com/mauricioabreu/golings) - [CONTIBUTING.md](https://github.com/mauricioabreu/golings/blob/main/CONTRIBUTING.md)

### Ziglings

