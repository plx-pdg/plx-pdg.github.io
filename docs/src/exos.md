# Exos management

This is a documentation driven design, this is the state of our research on the best exos management solution for the supported languages. This will probably be useful to future contributors who might want to understand why we made these decisions, help other `*lings` projects in their thinking,

## Defining "the best"
We believe the best structure will lead to the following qualities: 
1. Speed to create new exos and editing existing ones
1. Ease of learning the structure and synatx to create and maintain exos
1. Ease of developing a solution and adding checks.

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

### PRJS

### Cplings

### Ziglings


