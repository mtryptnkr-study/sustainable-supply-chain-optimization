# sustainable-supply-chain-optimization
Multi-objective MILP framework for cost–carbon supply chain optimization, Pareto analysis and disruption stress testing.

# Sustainable Multi-Objective Supply Chain Network Optimization

This project develops a **mixed-integer linear programming (MILP)** framework for a five-country supply chain and extends it beyond cost minimization to study **cost–carbon trade-offs, carbon pricing, demand robustness and freight-disruption resilience**.

The model is implemented in **PuLP** and evaluates production and distribution decisions across the USA, Germany, Japan, Brazil and India.

## Project Objectives

- Formulate a capacitated five-country supply-chain network using MILP.
- Minimize economic cost while satisfying demand and plant-capacity constraints.
- Quantify **cost–CO₂ trade-offs** using an ε-constraint Pareto framework.
- Evaluate the effect of carbon pricing on network configuration.
- Test robustness to demand growth and freight-cost disruption.
- Identify service-level feasibility limits under delivery-time constraints.

## Network Model

The model includes:

- Facility-capacity decisions
- Production and inter-country flows
- Variable manufacturing costs
- Freight costs
- Storage and fixed facility costs
- Regional demand
- CO₂-emission factors
- Delivery lead times

The primary economic objective is

$$
\min C =
\sum_{i,s} F_{is}y_{is}
+
\sum_{i,j} c_{ij}x_{ij}
$$

where \(y_{is}\) represents plant-capacity choices and \(x_{ij}\) represents inter-country supply flows.

Network emissions are calculated as

$$
E =
\sum_{i,j} e_{ij}x_{ij}.
$$

## Multi-Objective Cost–Carbon Analysis

An **ε-constraint approach** is used to construct the Pareto frontier.

Economic cost remains the objective while progressively tighter CO₂ budgets are imposed:

$$
E \leq \varepsilon.
$$

Each solution therefore represents the **least-cost network configuration achievable at a given emissions level**.

## Key Results

The extended model identified:

- Up to **38.6% modeled CO₂ reduction**
- At approximately a **10.0% cost premium**
- A minimum feasible uniform delivery-time allowance of approximately **34 days**
- Only about **2.15% uniform demand-growth headroom** under the existing candidate capacity structure
- A **56.2% increase in network cost** under a 3× freight-cost disruption scenario
- The first tested carbon-price response at approximately **$50/tCO₂**

These results should be interpreted as outcomes of the modeled supply-chain system rather than predictions of a specific real-world company network.

## Scenario Analysis

The project evaluates four major scenario classes:

1. **Cost–carbon Pareto optimization**
2. **Carbon-price scenarios**
3. **Demand and capacity robustness**
4. **Freight-cost disruption stress testing**

## Research Workflow

```text
Supply-Chain Data
        ↓
MILP Network Formulation
        ↓
Cost-Optimal Baseline
        ↓
Cost–Carbon Pareto Analysis
        ↓
Carbon-Price Scenarios
        ↓
Demand / Capacity Robustness
        ↓
Freight Disruption Stress Test
        ↓
Decision-Support Insights
```
