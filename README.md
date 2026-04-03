# Numerical-Solutions-to-Hyperbolic-PDEs

## 📖 Overview
This project investigates the numerical solution of **hyperbolic partial differential equations (PDEs)** using finite difference methods. The focus is on both **linear** and **nonlinear** problems:

$$
\textbf{Linear advection equation: } \quad \frac{\partial u}{\partial t} +  \frac{\partial (au)}{\partial x} = 0
$$

$$
\textbf{Non-linear Inviscid Burgers’ Equation: }\frac{\partial u}{\partial t} + \frac{\partial}{\partial x}\left(\frac{u^2}{2}\right) = 0
$$


This project combines **theoretical analysis** (stability and consistency) with **numerical simulations** to investigate accuracy, stability, and computational efficiency. The theoretical analysis—including **Von Neumann stability analysis using Fourier modes** and **consistency analysis**—is presented in the full report:

📄 **Full Project Report:** [Click here to view the PDF](./Project.pdf)


## Reflection on numerical methods being used
From **Von Neumann stability analysi** and **consistency analysis** we obtained First Upwind Scheme is First-order accurate  Stable for $c \leq 1$ 

$$
\textbf{ First Upwind Scheme }U_k^{n+1} = U_k^n - c \left(U_k^n - U_{k-1}^n \right). 
$$



---

### 2. Lax Method
$$
U_k^{n+1} = \frac{1}{2}(U_{k+1}^n + U_{k-1}^n) - \frac{c}{2}(U_{k+1}^n - U_{k-1}^n)
$$

- First-order accurate  
- Diffusive but stable  

---

### 3. Lax–Wendroff Method
$$
U_k^{n+1} = U_k^n - \frac{c}{2}(U_{k+1}^n - U_{k-1}^n) + \frac{c^2}{2}(U_{k-1}^n - 2U_k^n + U_{k+1}^n)
$$

- Second-order accurate  
- Captures sharp gradients effectively  

---

### 4. MacCormack Method

**Predictor:**

$$
U_k^* = U_k^n - \frac{\Delta t}{\Delta x} \left[f(U_{k+1}^n) - f(U_k^n)\right]
$$

**Corrector:**

$$
U_k^{n+1} = \frac{1}{2}\left(U_k^n + U_k^* - \frac{\Delta t}{\Delta x}(f(U_k^*) - f(U_{k-1}^*))\right)
$$

- Second-order accurate  
- Equivalent to Lax–Wendroff for linear problems  
- Performs well for nonlinear PDEs  

---

### 5. BTCS Scheme
- Implicit method  
- Unconditionally stable  
- First-order in time, second-order in space  

---

## 🔍 Stability Analysis

The Courant number is defined as:
$$
c = \frac{a \Delta t}{\Delta x}
$$

Stability condition (CFL condition):
$$
c \leq 1
$$

- If $c > 1$ → instability  
- Stability depends on $\Delta t$ and $\Delta x$  

---

## 📊 Numerical Experiments

### Linear Advection Equation
- Instability observed when $c > 1$  
- Smaller $\Delta t$ improves stability but increases diffusion  
- Lax–Wendroff provides best accuracy  
- BTCS remains stable for all $\Delta t$  

---

### Inviscid Burgers’ Equation

Flux function:
$$
f(u) = \frac{u^2}{2}
$$

- Larger $\Delta t$ leads to instability  
- Optimal choice:
$$
\Delta t = 0.1
$$

Observations:
- MacCormack and Lax–Wendroff capture steep gradients well  
- Lax method introduces noticeable numerical diffusion  

---

## 📈 Key Findings

- All explicit schemes are **conditionally stable**  
- Governed by the CFL condition  
- Trade-off between:
  - Accuracy  
  - Stability  
  - Computational efficiency  
- Second-order methods outperform first-order methods  

---

## 📂 Project Structure
