# Numerical-Solutions-to-Hyperbolic-PDEs

# 📊 Numerical Solution of Hyperbolic PDEs

## 📖 Overview
This project investigates the numerical solution of **hyperbolic partial differential equations (PDEs)** using finite difference methods. The focus is on both **linear** and **nonlinear** problems:

- Linear advection equation  
- Inviscid Burgers’ equation  

The project combines theoretical analysis (stability and consistency) with numerical simulations to study accuracy, stability, and computational efficiency.

---

## 🧠 Mathematical Formulation

### Linear Advection Equation  
du/dt + a * du/dx = 0

### Inviscid Burgers’ Equation  
du/dt + d/dx (u² / 2) = 0

### Conservation Form  
u_t + f(u)_x = 0

---

## ⚙️ Numerical Methods

### 1. First Upwind Scheme  
U(k, n+1) = U(k, n) - c [U(k, n) - U(k-1, n)]

- First-order accurate  
- Stable for c ≤ 1  
- Introduces numerical diffusion  

---

### 2. Lax Method  
U(k, n+1) = 0.5 [U(k+1, n) + U(k-1, n)]  
               - (c/2) [U(k+1, n) - U(k-1, n)]

- First-order accurate  
- More stable but diffusive  

---

### 3. Lax–Wendroff Method  
U(k, n+1) = U(k, n)  
               - (c/2)[U(k+1, n) - U(k-1, n)]  
               + (c²/2)[U(k-1, n) - 2U(k, n) + U(k+1, n)]

- Second-order accurate  
- Captures sharp gradients better  

---

### 4. MacCormack Method  

Predictor:  
U*(k) = U(k, n) - (dt/dx)[f(U(k+1, n)) - f(U(k, n))]

Corrector:  
U(k, n+1) = 0.5 [U(k, n) + U*(k)  
                        - (dt/dx)(f(U*(k)) - f(U*(k-1)))]

- Second-order accurate  
- Works well for nonlinear problems  

---

### 5. BTCS Scheme  
- Implicit method  
- Unconditionally stable  
- First-order in time, second-order in space  

---

## 🔍 Stability Analysis

Courant number:

c = (a * dt) / dx

Stability condition:

c ≤ 1

- If c > 1 → instability  
- Stability depends on dt and dx  

---

## 📊 Numerical Experiments

### Linear Advection
- Instability when c > 1  
- Smaller dt → more diffusion  
- Lax–Wendroff gives best accuracy  
- BTCS always stable  

---

### Inviscid Burgers’ Equation
- Flux: f(u) = u² / 2  
- Best time step: dt = 0.1  

Observations:
- MacCormack & Lax–Wendroff → sharper solutions  
- Lax → more diffusive  

---

## 📈 Key Findings

- Explicit schemes are conditionally stable  
- Governed by CFL condition  
- Trade-off between:
  - Accuracy  
  - Stability  
  - Efficiency  
- Second-order methods perform better  

---

## 📂 Project Structure
