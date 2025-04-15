---
title: "Useful Derivations"
description: "."
summary: "Useful derivations that I return to from time to time"
params:
    ShowReadingTime: false
    ShowShareButtons: true
    Description: "Useful derivations that I return to from time to time"
---


## Normal Equations

Suppose we are given an input matrix $\mathbf{X} \in \mathbb{R}^{N \times K}$ and target vector $\mathbf{y} \in \mathbb{R}^N$. We want to find the parameter vector $\mathbf{w} \in \mathbb{R}^K$ that minimizes the residual sum of squares (RSS):

$$
\text{RSS}(\mathbf{w}) = \sum_i (y_i - \mathbf{x}_i^T \mathbf{w})^2 = (\mathbf{y} - \mathbf{Xw})^T (\mathbf{y} - \mathbf{Xw})
$$

To minimize RSS, we expand the squared error and take the derivative:

$$
\text{RSS}(\mathbf{w}) = \mathbf{y}^T \mathbf{y} - 2 \mathbf{y}^T \mathbf{Xw} + \mathbf{w}^T \mathbf{X}^T \mathbf{Xw}
$$

Take the gradient and set it to zero:

$$
\nabla_{\mathbf{w}} \text{RSS}(\mathbf{w}) = -2\mathbf{X}^T \mathbf{y} + 2 \mathbf{X}^T \mathbf{Xw} = 0
$$

Solve for $\mathbf{w}$:

$$
\mathbf{X}^T \mathbf{Xw} = \mathbf{X}^T \mathbf{y}
$$

$$
\mathbf{w} = (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T \mathbf{y}
$$

This is known as the **normal equation**, and $ (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T $ is the **Moore-Penrose pseudo-inverse**.

> **Important Note:** In least squares, for the equation $A \mathbf{c} = \mathbf{b}$ to have a solution, $\mathbf{b}$ must lie in the **range** (column space) of $A$.

---

## Stochastic Gradient Descent 
Stochastic Gradient Descent (SGD) is an optimization technique where we update weights using just one (or a few) data points at a time. It's simple and scalable, but often inefficient.

**Update rule:**

$$
\mathbf{w}_{t+1} = \mathbf{w}_t - \eta \nabla _{\mathbf{w}} L(\mathbf{w}_t)
$$

### Why It's the "Worst Method" In High Dimensional Space

- In high-dimensional space, SGD effectively moves along **a single line direction** per step.
- This might work well in lower dimensions, but we are **unlikely to find a global minimum** in the high dimensional spaces that we often use for deep learning (which can be 10s of thousands of dimensions). This is akin to searching a lecture hall with a piece of string. 
- It can take many steps to converge or get stuck in poor local minima.

### A Note on Dataset Scaling and Generalization

One insight that has powered the LLM revolution has been the rise of emergent generalization capabilities from increasing the size of a pretraining dataset. Here's a potential explanation as to why: If we **increase the size of the input dataset**, it can change the optimization landscape in high dimensions:

- Each new batch may guide SGD toward a **different local minimum**.
- With more data, these local minima may **average out**, resulting in a better global solution.
- This could explain why **increasing dataset size** often improves generalization — not just by more data, but by **exploring more of the loss surface**.


Inspired by Eugen Hotaj - https://eugenhotaj.github.io/