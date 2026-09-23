# Supply Chain Optimization Solver

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Gurobi](https://img.shields.io/badge/Gurobi-ED1C24?style=for-the-badge&logo=gurobi&logoColor=white)
![Operations Research](https://img.shields.io/badge/Operations%20Research-MILP-blue?style=for-the-badge)

A Mixed-Integer Linear Programming (MILP) solver developed in **Python** using the **Gurobi Optimizer**. 

This project solves a complex, joint **Facility Location** and **Vehicle Routing Problem (TSP variation)** designed for the distribution network of a hypothetical company (*Polli Tech*). The model mathematically balances infrastructure investments with logistics operations to minimize the overall daily costs.

## Problem Statement

The solver must determine the optimal placement of warehouses from a set of candidate locations and compute the optimal daily route for a single delivery vehicle. The vehicle starts at the company headquarters, visits all the newly constructed warehouses to deliver goods, and returns to the headquarters.

The mathematical model jointly optimizes two sets of decision variables:
* **`X` (Facility Location):** A binary vector indicating which candidate warehouse locations are built and activated.
* **`Y` (Vehicle Routing):** A binary matrix representing the directed paths chosen by the delivery vehicle between the headquarters and the activated warehouses.

## Objective Function

The solver minimizes the total daily operating cost, formulating a trade-off between:
1. **Construction Costs:** Amortized daily cost for building and maintaining an active warehouse.
2. **Unserved Client Penalties:** Economic loss incurred for every supermarket that is not covered by any active warehouse.
3. **Travel Costs:** Fuel and logistics costs proportional to the total distance covered by the delivery vehicle.

## Project Structure & Data

The problem instances are evaluated based on three input files located in the `data/` directory:
* `weights.json`: Contains the economic weights (`construction`, `missed_supermarket`, `travel`).
* `service.csv`: A boolean incidence matrix where entry $i,j = 1$ if candidate warehouse $i$ can serve supermarket $j$.
* `distances.csv`: An asymmetric distance matrix representing the network topology.

The solver logic is encapsulated via Object-Oriented Programming (OOP) in a custom class inheriting from an `AbstractSolver` interface, ensuring seamless integration with the testing environment.

## Prerequisites

To run this solver, you need a valid **Gurobi license** (academic licenses are freely available for university students) and the following Python packages:

```bash
pip install gurobipy numpy pandas
```

## How to Run

1. Clone the repository:
   ```bash
   git clone [https://github.com/francescofoglia0/Supply-Chain-Optimization-Solver.git](https://github.com/francescofoglia0/Supply-Chain-Optimization-Solver.git)
   cd Supply-Chain-Optimization-Solver
   ```

2. Execute the main script to run the optimization model and generate the output variables (`X` and `Y`):
   ```bash
   python main.py
   ```

3. Run the evaluator to compute the objective function value and print the detailed cost breakdown (constructions, missed supermarkets, travel length):
   ```bash
   python evaluator.py
   ```

## Academic Context

This project was developed for the Operations Research course (BSc in Mathematical Engineering at Politecnico di Torino). It demonstrates the ability to translate real-world business and logistical requirements into a rigorous mathematical model and solve it using industry-standard computational tools.
