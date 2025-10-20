# DTBplus
Mathematica notebooks about Band Structure calculations using DFTB+.
This repository contains my Mathematica notebooks and related materials from the course Solid Physics at Yachay Tech University. 

## THEORY:

DFTB+ is an implementation of the Density Functional Tight Binding (DFTB) method, containing many extensions to the original method. The development is supported by various groups, resulting in a code which is probably the most versatile DFTB-implementation, with some unique features not available in other implementations so far.

## WHAT TO EXPECT IN THIS REPOSITORY:
Steps to obtain the Band Structure of atomic structures:

## INPUTS REQUIRED FOR RUNNING AN DFTB+ CALCULATION:
POSCAR FILE: this file contains the geometrical position and lattice of the structure.

running files:
xkps.sh
xcell.sh
xdos.sh
xband.sh

## Understanding the input files:
1. POSCAR file:
   This file contains the geometry and lattice parameters of the lattice given.
   The first line contains the name of the atom or atoms.
   The second line contains the scale factor.
   From third line to fifth line we have the lattice vectors a1, a2, a3.
   The sixth line contains the number of atoms per structure.
   The last to lines contains the positions in fractional coordinates.
2. kps.sh:
   This script iterates over a range of k-point values, generates input files for DFTB+ calculations, runs the calculations, and extracts specific data from the output files.
   The part to be edited is: for kp in $(seq 4 1 13); do    which starts a loop that iterates over the range of k-point values from 4 to 13 (inclusive) with a step of 1.
   The output file to be expected from this kps is a kps.dat which contains the energy extrapolated to 0K for the range of the kpoints.

3. xcell.sh:
   This script automates the process of running DFTB+ calculations for a range of lattice parameters for the converged kpoint. For each lattice parameter:
    It generates a POSCAR file with the current lattice parameter.
    It generates a DFTB+ input file with the specified k-point grid.
    It runs the DFTB+ calculation and saves the output.
    It extracts specific data from the output file and appends it to a data file.
    It moves and copies the detailed output and charges files to new names that include the current lattice parameter.

4. xdos.sh:
   This script is designed to calculate the Density of States (DOS) and PDOS for a given crystal structure using the DFTB+ method using the optimal lattice parameter and converged kpoint obtained.

5. xband.sh:
   This Bash script automates the process of calculating the band structure for a given crystal structure using the DFTB+ method. It starts by defining the optimal k-point value kp and the optimal lattice parameter lat.

