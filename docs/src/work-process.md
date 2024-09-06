# Work process
### Communication
1. We have a Telegram group to have group calls, discuss and ask for reviews
1. We do 2 small coordination meetings starting between 9:30 and 10:00, and another one around 15:00.

### Versionning
We follow semver (Semantic Versionning), see the specification on [semver.org](https://semver.org). All versions under `1.0.0` are not to be considered stable, breaking changes can appear in the CLI arguments, keyboard shortcuts, file structure, exo syntax, ... internal Rust code is not exposed externally as it is not a library, so we don't have to consider major changes in the code.

### Changelog
We follow the [Keep a Changelog](https://keepachangelog.com) convention, we write users oriented changelog at each release to describe changes in a more accessible way that git log outputs between releases.

### Commits
We try to follow the [Conventionnal commits](https://conventionalcommits.org).