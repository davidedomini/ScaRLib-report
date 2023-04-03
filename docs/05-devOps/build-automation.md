---
title: Build automation
parent: DevOps
has_children: false
nav_order: 2
---

# Build automation
To manage the project structure, we used Gradle, a tool mainly used for managing JVM-based languages. The project was organized into three sub-projects:
- `scarlib-core`: implements the core functionalities and abstractions of the framework, 
    such as the definition of the main data structures and the implementation of the main algorithms.
- `dsl-core`: implements the DSL functions that allows for agile and flexible creation of CMARL training systems.
- `alchemist-scafi`: implements the integration with the two tools [Alchemist] and [Scafi]. 
    Such integration enables the possibility to run the learning process in an aggregate computing context.

Thanks to Gradle, we were able to easily manage dependencies between the sub-projects and third-party libraries. We also utilized Gradle for customized tasks (e.g., jars generation).






[Scafi]: https://scafi.github.io/
[Alchemist]: http://alchemistsimulator.github.io/