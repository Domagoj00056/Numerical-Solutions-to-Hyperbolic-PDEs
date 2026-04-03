# Numerical-Solutions-to-Hyperbolic-PDEs

# 📊 Numerical Solution of Hyperbolic PDEs

## 📖 Overview
This project investigates the numerical solution of **hyperbolic partial differential equations (PDEs)** using finite difference methods. The focus is on both **linear** and **nonlinear** problems:

- Linear advection equation  
- Inviscid Burgers’ equation  

The project combines **theoretical analysis** (stability and consistency) with **numerical simulations** to study the performance of different schemes in terms of stability, accuracy, and computational efficiency.

---

## 🧠 Mathematical Formulation

### Linear Advection Equation
\[
\frac{\partial u}{\partial t} + a \frac{\partial u}{\partial x} = 0
\]

### Inviscid Burgers’ Equation
\[
\frac{\partial u}{\partial t} + \frac{\partial}{\partial x}\left(\frac{u^2}{2}\right) = 0
\]

### Conservation Form
\[
u_t + f(u)_x = 0
\]

---

## ⚙️ Numerical Methods

### 1. First Upwind Scheme
\[
U_k^{n+1} = U_k^n - c \left(U_k^n - U_{k-1}^n \right)
\]

- First-order accurate in space and time  
- Stable for \( c \leq 1 \)  
- Introduces numerical diffusion  

---

### 2. Lax Method
\[
U_k^{n+1} = \frac{1}{2}(U_{k+1}^n + U_{k-1}^n) - \frac{c}{2}(U_{k+1}^n - U_{k-1}^n)
\]

- First-order accurate  
- More stable than upwind  
- Diffusive behaviour  

---

### 3. Lax–Wendroff Method
\[
U_k^{n+1} = U_k^n - \frac{c}{2}(U_{k+1}^n - U_{k-1}^n) + \frac{c^2}{2}(U_{k-1}^n - 2U_k^n + U_{k+1}^n)
\]

- Second-order accurate in space and time  
- Captures sharp gradients more effectively  

---

### 4. MacCormack Method

Predictor:
\[
U_k^* = U_k^n - \frac{\Delta t}{\Delta x} \left[f(U_{k+1}^n) - f(U_k^n)\right]
\]

Corrector:
\[
U_k^{n+1} = \frac{1}{2}\left(U_k^n + U_k^* - \frac{\Delta t}{\Delta x}(f(U_k^*) - f(U_{k-1}^*))\right)
\]

- Second-order accurate  
- Equivalent to Lax–Wendroff for linear problems  
- Performs well for nonlinear equations  

---

### 5. BTCS Scheme
- Implicit method  
- Unconditionally stable  
- First-order accurate in time  
- Second-order accurate in space  

---

## 🔍 Stability Analysis

Using **Von Neumann stability analysis**, all explicit schemes satisfy the CFL condition:

\[
c = \frac{a \Delta t}{\Delta x} \leq 1
\]

- If \( c > 1 \): numerical solutions become unstable  
- Stability strongly depends on the choice of \( \Delta t \) and \( \Delta x \)  

---

## 📊 Numerical Experiments

### Linear Advection Equation
- Instability observed when \( c > 1 \)  
- Smaller \( \Delta t \) improves stability but increases numerical diffusion  
- Lax–Wendroff provides the best balance between accuracy and stability  
- BTCS remains stable for all \( \Delta t \), but may introduce oscillations  

---

### Inviscid Burgers’ Equation
- Nonlinearity handled using flux:
  \[
  f(u) = \frac{u^2}{2}
  \]
- Larger time steps lead to instability  
- Optimal time step found:
  \[
  \Delta t = 0.1
  \]

- MacCormack and Lax–Wendroff:
  - Better at resolving steep gradients  
- Lax method:
  - Shows noticeable numerical diffusion  

---

## 📈 Key Findings

- All explicit schemes are **conditionally stable**  
- Stability governed by the **CFL condition**  
- Trade-off exists between:
  - Accuracy  
  - Stability  
  - Computational cost  
- Second-order methods outperform first-order methods  
- Proper selection of discretisation parameters is essential  

---

## 📂 Project Structure
