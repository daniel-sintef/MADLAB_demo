# Tensile Test Simulation using ASE

## Overview
This project uses the **Atomic Simulation Environment (ASE)** to simulate a **tensile test** on an **FCC aluminum slab** with **randomly substituted copper atoms**. The simulation applies **manual strain** in the **z-direction** while constraining motion in the **x- and y-directions** for the topmost atoms. 

The simulation employs **Langevin Molecular Dynamics (MD)** at 300K to observe the response of the system under stress.

## Prerequisites
Before running the notebook, ensure you have Python installed with the following packages:
- `ase` (Atomic Simulation Environment)
- `numpy`

To install ASE, use:
```sh
pip install ase
```

## How It Works

### 1. **Building the FCC Aluminum Slab**
- The notebook constructs a **(4 × 4 × 20) FCC aluminum slab**.
- A vacuum layer of **10 Å** is added to prevent interactions between periodic images.
- A single atom is removed to introduce an intentional **weak point**.

### 2. **Random Cu Substitution**
- A specified fraction (~50%) of atoms are randomly replaced with **copper (Cu)** to introduce material variability.
- A **random seed** ensures reproducibility.

### 3. **Applying Constraints**
Two types of constraints are applied:
- **Bottom layers** are completely fixed (cannot move).
- **Top layers** are locked in the x- and y-directions but can be manually displaced in the z-direction to simulate strain.

### 4. **Molecular Dynamics Setup**
- The **Langevin thermostat** maintains the system at **300K** to mimic realistic thermal conditions.
- The **EMT calculator** is used for force evaluation (a simple embedded-atom method potential).
- The system undergoes **5000 MD steps**.

### 5. **Strain Application**
- Every **10 MD steps**, a small displacement in the **z-direction** is applied to the top layer.
- This simulates a **tensile test**, stretching the material over time.

### 6. **Trajectory Output**
- Every **100 MD steps**, the atomic positions are saved to an **XYZ file** (`fcc_al_tensile_test.xyz`).
- This trajectory can be visualized using **OVITO** or ASE’s built-in visualization tools.

## Running the Notebook
Open the notebook and run all cells sequentially to execute the simulation.

## Visualizing Results
To visualize the output in ASE:
```sh
ase gui fcc_al_tensile_test.xyz
```
Or use **OVITO**:
1. Open **OVITO**.
2. Load `fcc_al_tensile_test.xyz`.
3. Play the trajectory to observe atomic motion under strain.

## Key Takeaways
- **Langevin MD** is used to simulate realistic conditions.
- **Fixed and constrained atoms** mimic experimental tensile tests.
- **Cu substitutions** introduce atomic-scale heterogeneity.
- **Trajectory files** allow for post-simulation visualization and analysis.

This setup provides a simple yet effective way to study **mechanical behavior** at the atomic scale!


