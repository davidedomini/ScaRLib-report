---
title: Implementation Requirements
parent: Requirements
has_children: false
nav_order: 5
---

# Implementation Requirements

- The framework should be implemented in Scala.
    - `scarlib-core` and `alchemist-scafi` modules should use `Scala 2.13.10`.
    - `dsl-core` module should use `Scala 3.2.2`.
- Tests should be implemented using [ScalaTest].
- The framework should use [ScalaPy] for the binding with python libraries.
- The framework should use [PyTorch] for training the neural networks.
- The framework should use [TensorBoard] for charts visualization.
- The framework should use [Alchemist] (version 25.14.6, or later) for agents simulation.
- The framework should use [Scafi] for aggregate programming.
 
[ScalaPy]: https://scalapy.dev/
[PyTorch]: https://pytorch.org/
[TensorBoard]: https://www.tensorflow.org/tensorboard
[Scafi]: https://scafi.github.io/
[Alchemist]: http://alchemistsimulator.github.io/
[ScalaTest]: https://www.scalatest.org/
