# A Comparative Study of Some Iterative Methods for Solving Linear Systems

## Author: A. Ouardi  

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

Solving linear systems is a fundamental problem in scientific computing and engineering applications. We consider the nonsingular system of n linear algebraic equations:  
$$A x = b$$

Direct methods (e.g., Gaussian elimination and LU decomposition) are robust but computationally expensive for large systems with \( O(N^3) \) complexity. Iterative methods like **Steepest Descent (SD)**, **Conjugate Gradient (CG)**, **Full Orthogonalisation (FOM)**, and **Generalized Minimal Residual (GMRES)** offer efficient alternatives for sparse and large-scale systems.  

This report explores these algorithms, including their theoretical background, Python implementations, and numerical results. We also discuss their advantages, limitations, and possible extensions.

---
