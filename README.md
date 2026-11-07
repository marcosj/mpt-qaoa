# 📈 mpt-qaoa: Multi-Asset Portfolio Construction via Quantum Optimization

A quantum optimization framework solving Modern Portfolio Theory (MPT) asset allocation challenges using the **Quantum Approximate Optimization Algorithm (QAOA)**, developed for the Vanguard Challenge.

## 🏛️ Overview & Objective

Portfolio optimization under real-world market constraints—such as cardinality limits, sector exposures, transaction costs, and liquidity constraints—frequently results in NP-hard combinatorial search spaces. This repository maps MPT formulations into **Quadratic Unconstrained Binary Optimization (QUBO)** and **Ising Spin Glass** hamiltonians, benchmarking optimization performance across classical baselines and parameter-optimized QAOA circuits.

## ⚙️ Core Optimization Features

- **Return vs. Risk:** Balances annualized expected returns against covariance risk matrix penalties scaled by risk aversion coefficient $q$.
- **Transaction Costs:** Accounts for rebalancing frictions based on distance from current asset holdings ($w_0$).
- **Liquidity Guardrails:** Penalizes illiquid assets using inverse average daily trading volume metrics.
- **Cardinality Constraint:** Enforces strict asset selection limits ($K$ assets out of $N$).
- **Sector Allocations:** Restricts over-exposure across specific market sectors via configurable ceiling caps.
- **Position Bounds:** Enforces minimum/maximum position sizes to eliminate dust allocations.

## 📐 Mathematical Formulation

Using binary allocation variables $x_i \in \{0, 1\}$:

$$\min_{\boldsymbol{x}} \quad q \cdot \boldsymbol{x}^T \boldsymbol{\Sigma} \boldsymbol{x} - \boldsymbol{\mu}^T \boldsymbol{x}$$

**Subject to Constraints:**
1. **Transaction Cost:** $C_{\text{text}} = \sum_{i=1}^N c_i (x_i - x_{0,i})^2$
2. **Liquidity Penalty:** $x_i \cdot w_i \le \ell_i \cdot V_i$
3. **Cardinality:** $\sum_{i=1}^N x_i = K$
4. **Sector Exposure:** $\sum_{i \in S_m} x_i \le L_m \quad \forall m$
5. **Investment Guardrails:** $w_{\text{min}} \cdot x_i \le w_i \le w_{\text{max}} \cdot x_i$

## 📊 Tech Stack

* **Quantum Computing:** [PennyLane](https://github.com/PennyLaneAI/pennylane) for differentiable quantum circuits and hybrid optimization.
* **Numerical Computing:** NumPy, SciPy for matrix manipulation and QUBO-to-Ising mapping.
