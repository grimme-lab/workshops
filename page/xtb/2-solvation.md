---
layout: default
title: Solvation
parent: "xtb"
nav_order: 4
has_children: false
permalink: page/xtb/Solvation
---

# Implicit Solvent Models

When modeling processes in solution, it is essential to account for solvent effects in calculations. Solvent interactions significantly influence not only energies but also molecular geometries.  
In **xtb**, two implicit solvent models are available: **GBSA** and **ALPB**. These models can be easily applied to any calculation. They can be invoked using:  

```bash
xtb struc.xyz --alpb <solvent>
xtb struc.xyz --gbsa <solvent>
```

Parameterized solvent and method combinations are:

| Solvent         | GFN1(ALPB) | GFN1(GBSA) | GFN2(ALPB) | GFN2(GBSA) | GFN-FF |
|----------------|-----------|-----------|-----------|-----------|--------|
| Acetone       | x         | x         | x         | x         | x      |
| Acetonitrile  | x         | x         | x         | x         | x      |
| Aniline       | x         |           | x         |           | x      |
| Benzaldehyde  | x         |           | x         |           | x      |
| Benzene       | x         | x         | x         | x         | x      |
| CH₂Cl₂        | x         | x         | x         | x         | x      |
| CHCl₃        | x         | x         | x         | x         | x      |
| CS₂          | x         | x         | x         | x         | x      |
| Dioxane      | x         |           | x         |           | x      |
| DMF          | x         |           | x         | x         | x      |
| DMSO         | x         | x         | x         | x         | x      |
| Ether        | x         | x         | x         | x         | x      |
| Ethylacetate | x         |           | x         |           | x      |
| Furane       | x         |           | x         |           | x      |
| Hexadecane   | x         |           | x         |           | x      |
| Hexane       | x         |           | x         | x         | x      |
| Methanol     | x         | x         | x         | x         | x      |
| Nitromethane | x         |           | x         |           | x      |
| Octanol      | x         |           | x         |           | x      |
| Octanol (wet)| x         |           | x         |           | x      |
| Phenol       | x         |           | x         |           | x      |
| Toluene      | x         | x         | x         | x         | x      |
| THF          | x         | x         | x         | x         | x      |
| Water (H₂O)  | x         | x         | x         | x         | x      |


An up-to-date list of available solvents can be found in the [documentation](https://xtb-docs.readthedocs.io/en/latest/gbsa.html).  

{% include warning.html content='If you want to compute a solvent that is not yet parameterized in **xtb**, use a solvent with a similar dielectric constant that is parameterized. They can be found from several sources, *e.g.* [here](https://depts.washington.edu/eooptic/linkfiles/dielectric_chart%5B1%5D.pdf). Never do a gas phase computation in such cases.' %}

In principle, both solvent models perform similarly but do not reach the accuracy of more advanced and computationally expensive models like COSMO-RS or SMD.  

{% include note.html content='GBSA and ALPB treat the solvent as an electrostatic continuum that is self-consistently relaxed during the SCC, directly influencing the wavefunction. Thus, the Wafefunction and SCC energies are not identical compared to a gas-phase calculation. Non-electrostatic contributions are added after SCC convergence.' %}

More details on the theoretical background and accuracy of ALPB and GBSA can be found in this [publication](https://pubs.acs.org/doi/abs/10.1021/acs.jctc.1c00471).  

{% include tip.html content='Using a solvent model can improve SCC or geometry optimization convergence when gas-phase calculations fail to converge. The resulting wavefunction or structure can serve as a good starting point for a gas-phase calculation.' %}
