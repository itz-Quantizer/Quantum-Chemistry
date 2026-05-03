

## Methodology

This project computes ground-state energies of small molecules (H₂, N₂, and LiH) using the Variational Quantum Eigensolver implemented with Qiskit and Qiskit Nature.

### Workflow

1. **Molecular Setup**
   Molecular systems (H₂, N₂, LiH) are defined over a range of interatomic distances using the STO-3G basis set to generate potential energy curves.

2. **Electronic Structure Calculation**
   The PySCF driver is used to compute the required molecular integrals and construct the second-quantized Hamiltonian.

3. **Active Space Reduction**
   Active space transformations are applied to reduce the number of orbitals and electrons, balancing computational cost and accuracy for each molecule.

4. **Hamiltonian Mapping**
   The fermionic Hamiltonian is transformed into a qubit operator using the Jordan–Wigner transformation.

5. **Ansatz Construction**
   The variational circuit combines:

   * A Hartree–Fock method initial state
   * A hardware-efficient `n_local` ansatz with parameterized rotation gates and entangling layers

6. **Optimization**
   Classical optimization is performed using SLSQP. A warm-start strategy is employed, where optimal parameters from previous geometries initialize subsequent runs for improved convergence.

7. **Energy Evaluation**
   The optimized circuits are evaluated to obtain ground-state energies across bond distances, producing potential energy curves for each molecule.

---
