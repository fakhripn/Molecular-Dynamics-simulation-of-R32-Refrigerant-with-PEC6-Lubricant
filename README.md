# Effect of Pentaerythritol Tetrahexanoate (PEC6) Lubricant Concentration on Thermophysical Properties of R32 Refrigerant: A Molecular Simulation Study

This repository contains the structural data and input scripts for the molecular dynamics (MD) simulations investigating the thermophysical properties of R32 refrigerant and Pentaerythritol Tetrahexanoate (PEC6) lubricant mixtures.

## Repository Contents

* **`lmp.data`**: The LAMMPS data file containing the initial topology and atomic coordinates for the mixture system, comprising 10,445 atoms. It includes the assigned masses, pair coefficients, bond, angle, dihedral, and improper parameters necessary for the OPLS-AA force field.
* **`run.in`**: The main LAMMPS input script used to execute the MD simulation.

## Simulation Parameters

The simulations are designed to run in LAMMPS with the following configurations:
* **Units & Style:** The simulation uses `real` units and `full` atom styles.
* **Force Field Setup:** Interactions are modeled using the OPLS-AA force field utilizing a Lennard-Jones/Coulomb long-range pair style with a cutoff of 14.0 Å. Pair modifications are set up with geometric mixing rules.
* **Electrostatics:** Long-range Coulombic interactions are computed using the Particle-Particle Particle-Mesh (PPPM) method with an accuracy of 1e-6.
* **Property Calculations (EMD / Green-Kubo):** Thermophysical properties are calculated using the Equilibrium Molecular Dynamics (EMD) approach based on the Green-Kubo formalism. The input script is configured with specific correlation lengths and sample intervals to calculate properties by integrating time-correlation functions (such as the stress auto-correlation function for viscosity or the heat flux auto-correlation function for thermal conductivity) derived from the system's equilibrium fluctuations.

## Usage

To run the simulation, you must have a working installation of [LAMMPS](https://www.lammps.org/). 

Ensure both `run.in` and `lmp.data` are placed in the same directory, then execute the simulation via the command line:

```bash
lmp -in run.in
