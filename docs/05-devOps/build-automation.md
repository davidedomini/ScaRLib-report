---
title: Build automation
parent: DevOps
has_children: false
nav_order: 2
---

# Build automation
To manage the project structure, we used Gradle, a tool mainly used for managing JVM-based languages. The project was organized into three sub-projects:
- `scarlib-core`
- `dsl-core`
- `alchemist-scafi`

Thanks to Gradle, we were able to easily manage dependencies between the sub-projects and third-party libraries. We also utilized Gradle for customized tasks (e.g., jars generation).