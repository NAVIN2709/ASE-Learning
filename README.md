# ASE Learning

Learning and practical experimentation with the Atomic Simulation Environment (ASE) for atomistic simulations and machine-learning interatomic potentials.

## Overview

This repository contains hands-on experiments with ASE, covering atomic structures, crystal structure files, geometry relaxation, trajectories, and extended XYZ datasets used in machine-learning atomistic workflows.

The learning workflow progressed from basic ASE operations to working with structures and preparing data for MACE and other machine-learning interatomic potentials.

## Folder Structure

```text
ASE-Learning/
│
├── ase-tutorial.ipynb
│
├── MoS2_XYZ.xyz
│
├── Si_new.cif
│
├── relax.extxy
├── train.extxy
├── valid.extxy
├── test.extxy
│
├── relax.traj
│
├── structure.gif
│
└── README.md
```

## Files

### `ase-tutorial.ipynb`

Jupyter Notebook containing the ASE experiments and Python workflows covered during the learning process.

Topics include:

* Creating and manipulating atomic structures
* Reading and writing structure files
* Working with ASE `Atoms`
* Calculators
* Energy and forces
* Geometry relaxation
* Trajectory handling
* Working with atomistic datasets

### `MoS2_XYZ.xyz`

XYZ structure file containing atomic coordinates for a MoS₂ structure.

Used for practicing loading and working with atomic structures in ASE.

### `Si_new.cif`

CIF file containing a silicon crystal structure.

Used to practice loading crystal structures and working with periodic materials using ASE.

### `relax.traj`

ASE trajectory file containing the sequence of structures generated during a geometry relaxation.

It can be used to inspect how the atomic structure changes during optimization.

```text
Initial Structure
       ↓
Calculate Forces
       ↓
Update Positions
       ↓
Calculate Forces
       ↓
      ...
       ↓
Relaxed Structure
```

### `relax.extxy`

Extended XYZ dataset containing structures and associated atomistic information generated during the relaxation workflow.

### `train.extxy`

Extended XYZ dataset used for training machine-learning interatomic potentials.

### `valid.extxy`

Validation dataset used to monitor model performance during training.

### `test.extxy`

Test dataset used to evaluate the trained model on previously unseen configurations.

The dataset organization follows the typical machine-learning workflow:

```text
             Dataset
                |
        ┌───────┼───────┐
        ↓       ↓       ↓
      Train   Valid    Test
        |
        ↓
   Model Training
        |
        ↓
   Model Evaluation
```

### `structure.gif`

Visualization of an atomic structure or simulation/relaxation process.

## ASE Workflow

The main workflow explored in this repository is:

```text
Atomic Structure
      ↓
Read CIF / XYZ
      ↓
ASE Atoms Object
      ↓
Attach Calculator
      ↓
Calculate Energy & Forces
      ↓
Geometry Optimization
      ↓
Save Trajectory
      ↓
Export Structure / Dataset
```

## Geometry Relaxation

ASE optimization was used to relax atomic structures by iteratively minimizing the forces acting on the atoms.

A typical workflow is:

```python
from ase.io import read
from ase.optimize import BFGS

atoms = read("structure.cif")

atoms.calc = calculator

optimizer = BFGS(atoms)
optimizer.run(fmax=0.05)

atoms.write("relaxed.cif")
```

The relaxation trajectory can then be inspected using the generated `.traj` file.

## File Formats

This repository also covers several common formats used in atomistic simulations.

| Format    | Purpose                                                                  |
| --------- | ------------------------------------------------------------------------ |
| `.ipynb`  | Python/Jupyter experiments                                               |
| `.xyz`    | Atomic coordinates                                                       |
| `.cif`    | Crystal structures and unit-cell information                             |
| `.traj`   | ASE simulation trajectories                                              |
| `.extxyz` | Atomic structures with additional properties such as energies and forces |
| `.gif`    | Visualization of structures/simulations                                  |

## Connection to MACE

The ASE workflow provides the foundation for working with machine-learning interatomic potentials such as MACE.

```text
             Structure
                 ↓
              ASE
                 ↓
        Machine-Learning
        Interatomic Potential
                 ↓
        ┌────────┼────────┐
        ↓        ↓        ↓
      Energy   Forces   Stress
        ↓        ↓        ↓
        └────────┼────────┘
                 ↓
        Relaxation / MD
```

ASE therefore acts as the simulation framework while MACE can provide the machine-learning-based energy and force calculations.

## Tools

* Python
* ASE
* NumPy
* Jupyter Notebook
* MACE
* Extended XYZ
* CIF
* XYZ

## Learning Path

```text
ASE Basics
    ↓
Atoms Objects
    ↓
CIF / XYZ Structures
    ↓
Calculators
    ↓
Energy & Forces
    ↓
Geometry Relaxation
    ↓
Trajectories
    ↓
Extended XYZ Datasets
    ↓
Train / Validation / Test Data
    ↓
MACE + ASE
```
