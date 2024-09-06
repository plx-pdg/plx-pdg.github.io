# Architecture

## Running architecture

![app system](img/png/app-systems.png)

![workflow](img/png/workflow.png)
## File architecture

```sh
.
├── .course-state.toml # save index skill and exo index
├── course.toml # define your course info and skill order
├── pointers
│   ├── crash-debug
│   │   ├── .exo-state.toml # save status of exo
│   │   ├── exo.toml # exo definition
│   │   ├── main.c
│   │   └── main.sol.c
│   ├── crash-debug-java
│   │   ├── .exo-state.toml
│   │   ├── exo.toml
│   │   ├── Main.java
│   │   ├── Main.sol.java
│   │   └── Person.java
│   └── skill.toml # define your skill info and exo order
├── other skills
├── build
   ...
```

## Defining all toml

### course.toml 
To create a course we need a name and a selection of skills (chapters) in a specific order.

```toml
name = "Full fictive course"
skills = ["intro", "pointers", "parsing", "structs", "enums"]
```

### skill.toml
To create a new skill, we need a name and a list of all the names of each exercices in a specific order.

```toml
name = 'Introduction'
exos = ['basic-args', 'basic-output']
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
## Generated toml

### .course-state.toml
This state is used to save the skill and exercise index for resume.

```toml
curr_skill_idx = 0
curr_exo_idx = 0
```

### .exo-state.toml
For each exercice, there is a state that can be in-progress, done or not done. There is also an optional favorite option to place the exercice into our personal selection.

```toml
state = "InProgress"
favorite = false
```

