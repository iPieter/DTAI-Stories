---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "DeepProbLog"
subtitle: "Neural Probabilistic Logic Programming"
summary: "This is the summary of the post, which is a featured post"
authors: ["Demo"]
tags: ["ProbLog", "Neuro-symbolic"]
categories: ["ProbLog", "Demo"]
date: 2019-08-03T10:36:34+02:00
lastmod: 2019-08-03T10:36:34+02:00
featured: true
draft: false


projects: []
---

# DeepProbLog

DeepProbLog is a neuro-symbolic framework that integrates the probabilistic logic programming language ProbLog with neural networks.

The full paper can be found [here](https://arxiv.org/abs/1907.08194).

The main strengths of DeepProbLog are:

- It combines probabilistic reasoning, logical reasoning and the power of neural networks.
- It can train neural networks and learn probabilistic paramters from examples.
- We retain both logic and neural networks as edge cases.

## What is DeepProbLog?

DeepProbLog is an extension of ProbLog that integrates neural networks through the concept of the neural predicate. It allows us to combine high-level logical reasoning with the sub-symbolic power of neural networks.

For example:
```
nn(mnist_classifier,[X],Y,[0..9]) :: digit(X,Y).
```

The neural predicate defined above declares that there's a neural network that will take in an input X, and has at its output a probability distribution. This relation can be used in the remainder of the program using the digit relation.

TODO: ADD figure for digit predicate distribution

We could for example define the addition over two MNIST digits:
```
nn(mnist_classifier,[X],Y,[0..9]) :: digit(X,Y).
addition(X,Y,Z) :- digit(X,N1), digit(Y,N2), Z is N1+N2.
```
Where the addition relation now defines the probability distribution over the sum of the individual digits.

TODO: add figure for addition predicate distribution

## Examples

#### MNIST addition

We compared the MNIST addition example describe above with a convolutional neural network baseline.
The result shows that the inclusion of the logic allows the model to train quicker and achieve a higher accuracy. It's also important to note that the neural network trained inside the DeepProbLog model can recognize single digits, whereas the convolutional baselines can only classify sums. The separation between the logic and neural aspects results in a more flexible model.
![MNISTS result](mnist.png)

#### Sketching

We reimplemented the experiments from the Differentiable Forth paper. These use a sketching approach to learn the missing behaviour from partial programs using small neural modules.

From the result we can see that we perform similar to the original (neural) model. For learning to sort lists, Differentiable Forth starts to struggle starting from length 4. This is due to the long program trace. DeepProbLog does not have this problem thanks to the fact that it can perform almost all of the program in the logic.
![Differentiable Forth result](d4.png)
