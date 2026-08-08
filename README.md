# Vanguard Challenge: Multi-Asset Portfolio Construction

This repository contains a quantum optimization approach to constructing a multi-asset portfolio. It leverages the Quantum Approximate Optimization Algorithm (QAOA) to optimize a Quadratic Unconstrained Binary Optimization (QUBO) formulation of Modern Portfolio Theory.

## Overview
The model balances expected returns against covariance risk while enforcing:
- Transaction cost: Rebalances distance from current holdings
- Liquidity limit: Penalizes illiquid assets based on daily trading volume Vi
- Diversification: Enforces holding exactly K asset classes
- Sector/exposure limits: Prevents over-exposure to Sector m
- Investment guardrails: Enforces minimum position sizes and prevents dust allocations
