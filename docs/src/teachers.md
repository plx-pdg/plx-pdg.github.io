# Experience for teachers 

**Warning: this is experience has not been implemented for the moment... some of it will be post-PDG development period.** 

<!--todo: refactor and add more details and examples of pain points-->

## Introduction
From a first look at PLX, it seems the delightful experience only benefit students... It is true that the project conception mainly focuses on students because they are the learners, but we thought about teachers too. Here are the key points why you should consider PLX and how it could help you build better courses driven by practice and augmented by feedback for your students !

## Enhance your exercises by easily adding automated checks
Instead of installing a test runner, configuring compilation, you can already cover some cases just by checking the output defining program arguments in various situations. Used to verify the common and edge cases.

<!--todo: add exo example where basic output checks and stdin injection would be far enough -->
<!-- show what teachers don't need to explain anymore (the scenarios to run manually to make sure it works -> encoded as tests) -->
<!-- "how would you write tests for this ?" to connect to the issue of "it's not that trivial end to end testing", -->
<!-- show how easy is it to define output checks -->

## Simplify or remove build configurations
For most cases, PLX can guess how to build the exo, you don't need to provide a `Makefile` or `CMakeLists.txt`, nor a `pom.xml`. You can customize the build via a `xmake.lua` if necessary, making it very easy to add a dependency like GoogleTest without requiring students to install it.

<!--todo: add explanations on why a VM with a single environment is not necessary anymore -->
<!--todo: add example of exo + 2 associated tests-->
<!--todo: add an example of necessary config and the amount of things removed with xmake and plx exo metadata -->

## Simplify management of exo files and solutions
Quickly edit an exo from the list, use templates for faster exo redaction and run checks on starting file and solution file.

<!--todo: compare with PDF based exo redaction and verification -->
<!--todo: show example of template -->
<!--todo: show GIF of a quick edit -->

## Enable general overview and easy review
If all your students fork a main repository and regularly push their answers, you can clone all those repositories and new opportunties for review could be possible. This is not supported either, but we could imagine a review mode where PLX could run all tests for all exos for all students! This would allow to generate a statistic grid to see the global progress. It enables the human review of each answer in a row to generate discussions and feedback in class.

<!--todo: show mockups of ideas for this review mode -->
<!--todo: explain workflow of review answers + oral feedback in class-->
