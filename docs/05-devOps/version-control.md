---
title: Versioning and Releasing
parent: DevOps
has_children: false
nav_order: 4
---

# Versioning and Releasing

Software versioning refers to the process of assigning a unique identifier to a software state. The identifier is typically an alphanumeric sequence of characters separated by dots, slashes, or dashes.

In our case, to distinguish different versions of the software, we decided to follow the guidelines proposed by [Semantic Versioning](https://semver.org/). Consequently, the software version is represented by three numbers separated by a dot: MAJOR.MINOR.PATCH.

The correct version to be associated with the software state is based on the saved commits, which were written following the Conventional Commit approach. In particular, we used the following approach:

**MAJOR** release
* Any commit type and scope terminating with `!` causes a `BREAKING CHANGE`

**MINOR** release
* Commit type `chore` with scope `api-deps` (*Dependency updates*)
* Commit type `feat` (*Features*) with any scope

**PATCH** release
* Commit type `chore` with scope `core-deps` (*Dependency updates*)
* Commit type `fix` (*Bug Fixes*) with any scope
* Commit type `docs` (*Documentation*) with any scope
* Commit type `perf` (*Performance improvements*) with any scope
* Commit type `revert` (*Revert previous changes*) with any scope

No release
* Commit type `test` (*Tests*)
* Commit type `ci` (*Build and continuous integration*)
* Commit type `build` (*Build and continuous integration*)
* Commit type `chore` with scope `deps` (*Dependency updates*)
* Commit type `chore` (*General maintenance*) with scopes different than the ones mentioned above 
* Commit type `style` (*Style improvements*) with any scope 
* Commit type `refactor` (*Refactoring*) with any scope 
