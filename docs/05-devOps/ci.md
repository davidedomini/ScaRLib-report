---
title: Continuous Integration
parent: DevOps
has_children: false
nav_order: 3
---

# Continuous Integration

Continuous Integration is an important practice in software development that involves frequently compiling, testing, and distributing source code to ensure that modifications do not introduce errors into existing software.

To automate this process, GitHub Actions were utilized.

The workflow created first runs the available tests for the ScaRLib project. If these tests are successful, the semantic-release tool is executed, which will automatically create a new release of the software if needed. As a final step, the workflow checks if all previous jobs were successful.