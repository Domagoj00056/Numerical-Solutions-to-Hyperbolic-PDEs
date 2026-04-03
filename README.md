# Numerical-Solutions-to-Hyperbolic-PDEs

**Predictor step**

$$
U_k^{*} = U_k^n - \frac{\Delta t}{2\Delta x}\big((U_{k+1}^n)^2 - (U_k^n)^2\big)
$$

$$
U_k^{n+1} = \frac{1}{2} (U_k^n + U_k^{*}) - \frac{\Delta t}{4\Delta x}\big(U_k^{*2} - U_{k-1}^{*2}\big)
$$

## 📖 Overview
This project investigates the numerical solution of **hyperbolic partial differential equations (PDEs)** using finite difference methods. The focus is on both **linear** and **nonlinear** problems:

$$
\textbf{Linear advection equation: } \quad \frac{\partial u}{\partial t} +  \frac{\partial (au)}{\partial x} = 0
$$

$$
\textbf{Non-linear Inviscid Burgers’ Equation: }\frac{\partial u}{\partial t} + \frac{\partial}{\partial x}\left(\frac{u^2}{2}\right) = 0
$$


This project combines **theoretical analysis** (stability and consistency) with **numerical simulations** to investigate accuracy, stability, and computational efficiency. The theoretical analysis, including **Von Neumann stability analysis using Fourier modes** and **consistency analysis** is presented in the full report:

📄 **Full Project Report:** [Click here to view the PDF](./Project.pdf)


## Reflection on numerical methods being used

From **Von Neumann stability analysis** and **consistency analysis**, we obtain the following properties for each scheme:

---

### First Upwind Scheme

- First-order accurate (in space and time)  
- Stable for $c \leq 1$  
- Introduces numerical diffusion  

$$
\textbf{First Upwind Scheme:} \quad 
U_k^{n+1} = U_k^n - c \left(U_k^n - U_{k-1}^n \right)
$$

---

### Lax Method

- First-order accurate  
- Stable for $c \leq 1$  
- More diffusive than higher-order methods  

$$
\textbf{Lax Method:} \quad 
U_k^{n+1} = \frac{1}{2}(U_{k+1}^n + U_{k-1}^n) - \frac{c}{2}(U_{k+1}^n - U_{k-1}^n)
$$

---

### Lax–Wendroff Method

- Second-order accurate (in space and time)  
- Stable for $c \leq 1$  
- Better at capturing sharp gradients  

$$
\textbf{Lax–Wendroff Method:} \quad 
U_k^{n+1} = U_k^n - \frac{c}{2}(U_{k+1}^n - U_{k-1}^n) + \frac{c^2}{2}(U_{k-1}^n - 2U_k^n + U_{k+1}^n)
$$

---

### BTCS Scheme

- First-order accurate in time, second-order in space  
- Unconditionally stable  
- May introduce non-physical oscillations  

$$
\textbf{BTCS Scheme:} \quad 
\frac{c}{2} U_{k-1}^{n+1} - U_k^{n+1} - \frac{c}{2} U_{k+1}^{n+1} = -U_k^n
$$

## Transformation of Lax and MacCormack Methods from Advection to Inviscid Burgers’ Equation

Both equations are first written in conservation form:

$$
\text{Advection:} \quad \frac{\partial u}{\partial t} + \frac{\partial (a u)}{\partial x} = 0
$$

$$
\text{Inviscid Burgers’:} \quad \frac{\partial u}{\partial t} + \frac{\partial}{\partial x}\left(\frac{u^2}{2}\right) = 0
$$

That is,

$$
u_t + f(u)_x = 0
$$

with flux functions:
- $f(u) = au$ (advection)  
- $f(u) = \frac{u^2}{2}$ (Burgers’ equation)

The Lax and MacCormack schemes are first derived for the advection equation using $f(u) = au$, and then extended to the inviscid Burgers’ equation by replacing the flux with $f(u) = \frac{u^2}{2}$.

Hence, the Lax scheme for the inviscid Burgers’ equation becomes:

$$
U_k^{n+1} = \frac{1}{2}\left(U_{k+1}^n + U_{k-1}^n\right) - \frac{\Delta t}{4\Delta x}\left((U_{k+1}^n)^2 - (U_{k-1}^n)^2\right)
$$

Similarly, the MacCormack method is given by:




**Predictor step**

$$
U_k^{*} = U_k^n - \frac{\Delta t}{2\Delta x}\big((U_{k+1}^n)^2 - (U_k^n)^2\big)
$$

**Corrector step**

$$
U_k^{n+1} = \frac{1}{2}\big(U_k^n + U_k^{*} - \frac{\Delta t}{2\Delta x}\big((U_k^{*})^2 - (U_{k-1}^{*})^2\big)\big)
$$


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
