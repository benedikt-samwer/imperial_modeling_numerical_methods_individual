# Modelling & Numerical Methods Assessment

**Imperial College London**

**MSc Applied Computational Science and Engineering (ACSE)**

**Module:** Modelling & Numerical Methods (2024/25)

---

## Overview

This repository contains the individual assessment components for the "Modelling & Numerical Methods" module. The project demonstrates the implementation of numerical methods for solving Partial Differential Equations (PDEs) governing physical phenomena, specifically focusing on stability analysis in 1D systems and computational fluid dynamics (CFD) in 2D.

## Repository Structure

*   `Q1b.ipynb`: Stability analysis of explicit time-stepping schemes for Advection-Diffusion systems.
*   `Q2d.ipynb`: Implementation of a 2D Incompressible Navier-Stokes solver using the pressure correction method.

## Q1b: Stability Analysis of Advection-Diffusion Systems

**Problem Statement:**
Investigation of numerical stability for the 1D Advection-Diffusion / Wave equation. The goal was to understand the impact of time-step size ($\Delta t$) and physical parameters on the stability of explicit numerical schemes.

**Implementation Details:**
*   **Discretization:** Finite Difference Method (FDM) on a 1D spatial grid.
*   **Time-Stepping:**
    *   **Forward Euler:** Used for the initial time step.
    *   **Adams-Bashforth (2nd Order):** Implemented for subsequent time steps to improve accuracy while maintaining explicit handling of terms.
*   **Stability Criteria:**
    *   Analysis of dimensionless groups: **Advection Courant Number** ($\lambda_a$), **Wave Courant Number** ($\lambda_w$), and **Diffusion Numbers** ($\lambda_d$).
    *   Verified theoretical stability limits (CFL condition) through numerical experiments.
*   **Visualization:** Time-evolution plots of the wave propagation (Gaussian pulse) to visualize the onset of numerical instability when stability conditions are violated.

## Q2d: 2D Incompressible Flow & Scalar Transport

**Problem Statement:**
Simulation of 2D incompressible fluid flow coupled with a scalar transport equation (Advection-Diffusion-Reaction). This problem models the transport of a chemical species or pollutant within a moving fluid.

**Implementation Details:**
*   **Navier-Stokes Solver (Projection Method):**
    1.  **Intermediate Velocity Step:** Explicit calculation of tentative velocities ($u^*, v^*$) including **Advection** (handled via upwind/central difference logic) and **Diffusion** (viscous) terms.
    2.  **Pressure Correction:** Solved the **Pressure Poisson Equation (PPE)** to enforce the incompressibility constraint ($\nabla \cdot \mathbf{u} = 0$).
        *   Implemented an **Iterative Jacobi Solver** to resolve the pressure field with Neumann boundary conditions.
    3.  **Velocity Correction:** Updated velocities using the computed pressure gradient.
*   **Scalar Transport:**
    *   Implemented a separate solver for the concentration field $C$, accounting for advection by the fluid, molecular diffusion ($D$), and a reaction term ($k$).
*   **Boundary Conditions:** Handled specific inflow/outflow and wall boundary conditions for both velocity and pressure fields.

## Technologies Used
*   **Python 3**
*   **NumPy:** High-performance vectorization for grid-based calculations.
*   **Matplotlib:** Visualization of fields and convergence plots.
*   **SciPy:** Sparse linear algebra operations (where applicable).

