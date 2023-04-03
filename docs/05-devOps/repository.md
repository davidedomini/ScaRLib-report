---
title: Repository Management
parent: DevOps
has_children: false
nav_order: 1
---

# Repository Management

To track the development of our project, we used a Github repository and created a dedicated organization called `ScaRLib-group`. The main repository is `ScaRLib`, which was divided into several branches: the `main` branch contains project releases, and the `develop` branch was used for ongoing development. For each necessary feature that needed to be added, a new branch was created from `develop` called `feature/feature-name`, and the same was done for bug fixes.

![GitFlow](/imgs/git-flow.png)

Commits were written following the [Conventional Commit](https://www.conventionalcommits.org/en/v1.0.0/) approach. A commit is therefore written in the following format:

```bash
<type>[optional scope]: <description>
```

The types of commits that have been adopted in our case are as follows:

- **build**: for changes related to the build system or external dependencies;
- **chore**: for changes that do not affect the production code;
- **ci**: for changes related to continuous integration;
- **docs**: for changes that only affect the documentation;
- **feat**: for the addition of a new feature;
- **fix**: when a bug is fixed;
- **perf**: for changes made to the code to improve performance;
- **refactor**: for changes to the code that do not relate to either bug fixes or the addition of a new feature (e.g., moving a method from one class to another);
- **style**: for changes that do not affect the meaning of the code (e.g., removing white spaces, formatting, etc.);
- **test**: for the addition of new tests or correction of existing tests.

## Seconday Repositories

In addition to the main `ScaRLib` repository, there are some secondary repositories in the organization that are useful for speeding up the use of the tool. The `ScarLib-experiments-startup` repository is a template that can be used to initialize a new project that uses ScaRLib from scratch. On the other hand, the `ScaRLib-flock-demo` repository contains a simple example of learning using ScaRLib and can be used as a crash-guide to understanding the main mechanisms offered by the tool.