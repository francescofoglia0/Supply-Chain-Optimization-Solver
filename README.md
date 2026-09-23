# Supply Chain Optimization Solver

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Gurobi](https://img.shields.io/badge/Gurobi-ED1C24?style=for-the-badge&logo=gurobi&logoColor=white)
![Operations Research](https://img.shields.io/badge/Operations%20Research-MILP-blue?style=for-the-badge)

A Mixed-Integer Linear Programming (MILP) solver developed for the Operations Research course (2024/2025). The project solves a complex, joint **Facility Location** and **Vehicle Routing Problem (TSP variation)** for a supply chain distribution network.

## Problem Statement

The goal is to design an optimal distribution chain for *Polli Tech*. The solver must determine the optimal placement of warehouses from a set of candidate locations and compute the optimal daily route for a single delivery vehicle. The vehicle starts at the company headquarters, visits all the newly constructed warehouses to deliver goods, and returns to the headquarters.

The mathematical model jointly optimizes two sets of decision variables:
* **`X` (Facility Location):** A binary vector indicating which candidate warehouse locations are activated.
* **`Y` (Vehicle Routing):** A binary matrix representing the directed paths chosen by the delivery vehicle between the headquarters and the activated warehouses.

## Objective Function

The solver minimizes the total daily operating cost, which is a trade-off between:
1. **Construction Costs:** Amortized daily cost for building and maintaining an active warehouse.
2. **Unserved Client Penalties:** Economic loss incurred for every supermarket that is not covered by any active warehouse.
3. **Travel Costs:** Fuel and logistics costs proportional to the total distance covered by the delivery vehicle.

## Data Structure

The problem instances are defined by three input files:
* `weights.json`: Contains the cost weights (`construction`, `missed_supermarket`, `travel`).
* `service.csv`: A boolean incidence matrix where entry $i,j = 1$ if candidate warehouse $i$ can serve supermarket $j$.
* `distances.csv`: An asymmetric distance matrix where the first row/column corresponds to the company headquarters and the remaining indices represent candidate warehouse locations.

## Architecture & Technologies

* **Language:** Python
* **Solver:** Gurobi Optimizer (`gurobipy`)
* **Data Processing:** NumPy, pandas
* **Design Pattern:** Object-Oriented Programming (OOP). The mathematical model is encapsulated in a custom solver class inheriting from an `AbstractSolver` interface, ensuring seamless integration with the testing environments.

