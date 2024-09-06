## CI/CD strategy
Most of the release process should be automated, this is why we configured GitHub actions to run different jobs.

### PR validation strategy
1. On each PR (and when new commits arrive) and on push on main, `cargo build` and `cargo test` are run to make sure everything is working
1. On each git tag, we will run a CI job to test, build and run `cargo publish` to release PLX on [crates.io](https://crates.io/crates/plx)

<!--todo: document release process
todo: document other OS-->
### GitHub workflow
1. We protect the main branch on the main repository to avoid pushing commits directly without any review. The 2 others repository (website + organisation profile) are not protected for ease of change.
1. For each feature or change:
  1. we create a new issue and assign it to the correct person
  1. create a new branch,
  1. try to follow the conventionnal commits standard for writing commit messages,
  1. when done we send a PR.
  1. The PR is automatically merged only after one review, and trivial changes that do not review can be merged by the PR creator.
  1. Github is configured to block merging if CI jobs are failing.
  1. We try to delete the branch when PR is merged.

![workflow](../../presentation/contributing-workflow.png)
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

![workflow](../../presentation/release-workflow.png)