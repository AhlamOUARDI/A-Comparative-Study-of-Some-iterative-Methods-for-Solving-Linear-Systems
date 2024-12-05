# A Comparative Study of Some Iterative Methods for Solving Linear Systems

## Author: A. Ouardi  
**Date:** _`<Today's Date>`_  

---

## Abstract

This document provides a detailed discussion on several algorithms, including their implementation and analysis, to solve linear algebraic equations. The iterative methods considered are the **Steepest Descent Gradient (SDG)**, the **Conjugate Gradient (CG)**, and the **Krylov subspace methods**.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Description of Algorithms](#description-of-algorithms)
    - [Steepest Descent](#steepest-descent)
    - [Conjugate Gradient](#conjugate-gradient)
    - [Krylov Subspace Methods](#krylov-subspace-methods)
3. [Tests and Comparison](#tests-and-comparison)

---

## Introduction

Solving linear systems is a fundamental problem in scientific computing and engineering applications. We consider the nonsingular system of \( n \) linear algebraic equations:  

\[
A x = b
\]

Direct methods (e.g., Gaussian elimination and LU decomposition) are robust but computationally expensive for large systems with \( O(N^3) \) complexity. Iterative methods like **Steepest Descent (SD)**, **Conjugate Gradient (CG)**, **Full Orthogonalisation (FOM)**, and **Generalized Minimal Residual (GMRES)** offer efficient alternatives for sparse and large-scale systems.  

This report explores these algorithms, including their theoretical background, Python implementations, and numerical results. We also discuss their advantages, limitations, and possible extensions.

---

## Description of Algorithms

### Steepest Descent

For the linear system \( A x = b \), where \( A \) is a real symmetric and positive definite matrix, we define:

\[
\Phi(x) := \frac{1}{2} \langle A x, x \rangle - \langle b, x \rangle
\]

where \( \langle ., . \rangle \) is the Euclidean scalar product. The following theorem holds:  

**Theorem:** If \( A \) is positive definite, then:  

\[
\Phi(x^*) = \min_{x \in \mathbb{R}^n} \Phi(x) \implies A x^* = b
\]

The steepest descent algorithm is as follows:

```python
def SDG(A, b, iter_max, tol, x=0):
    r = b.copy()
    iter = 0
    err = np.linalg.norm(r)
    L = [np.linalg.norm(r)]
    while iter < iter_max and err > tol:
        iter += 1
        Ar = A @ r  # Ar_k
        err2 = np.dot(r, r)
        alpha = err2 / np.dot(Ar, r)
        x += alpha * r
        r -= alpha * Ar
        err = np.sqrt(err2)
        L.append(err)
    return L, iter
