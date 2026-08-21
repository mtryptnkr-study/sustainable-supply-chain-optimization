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

### Cost–Carbon Pareto Frontier

The ε-constraint formulation quantifies the economic cost of network decarbonization. The model identifies up to **38.64% CO₂ reduction** relative to the cost-optimal baseline at approximately a **10.04% increase in monthly network cost**.

![Cost–carbon Pareto frontier](cost_carbon_pareto.png)

### Carbon-Price Response

Carbon-price scenarios were evaluated to determine when emissions penalties become large enough to change the economically optimal sourcing and production configuration.

![Carbon-price response](carbon_price_response.png)

### Freight-Disruption Stress Test

A severe logistics disruption was represented by increasing freight costs by **3×** and re-optimizing the network. The resulting optimal configuration increased modeled network cost by approximately **56.15%** and altered the geographic production allocation.

![Freight-disruption response](freight_disruption.png)

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
## Tools
- Python
- Pandas
- NumPy
- Matplotlib
- PuLP
- CBC MILP Solver
- OpenPyXL
- Jupyter Notebook

## Repository Structure
├── Sustainable_Supply_Chain_Optimization.ipynb
├── README.md
├── requirements.txt
├── .gitignore
└── LICENSE

## Limitations

The model is a deterministic and stylized supply-chain network.

It does not currently include:

- stochastic demand distributions,
- multi-period inventory dynamics,
- supplier-failure probabilities,
- endogenous transport-mode selection,
- nonlinear economies of scale,
- uncertainty in CO₂-emission factors.

Potential future extensions include robust optimization, stochastic programming and Monte Carlo scenario analysis.

## Author

Maitrey Patankar
M.Tech Sustainable Engineering, IIT Hyderabad
