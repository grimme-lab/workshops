---
layout: default
title: General
parent: "xtb"
nav_order: 2
has_children: false
permalink: /page/xtb/general
---

# Using **xtb**

## Getting Help
To get help and an overview of the different flags available in **xtb**, you can refer to the [documentation](https://xtb-docs.readthedocs.io/en/latest/index.html) or use the following command:

```bash
xtb --help
```

## Input File

**xtb** supports various molecular structure file formats:

| Format                  | Basename           | Suffix               | Molecular | Periodic |
|-------------------------|--------------------|----------------------|-----------|----------|
| Turbomole              | coord              | coord, tmol         | x         | 3D       |
| xyz file              |                    | xyz                  | x         |          |
| mol file              |                    | mol                  | x         |          |
| Structure-Data file    |                    | sdf                  | x         |          |
| Protein Database file  |                    | pdb                  | x         |          |
| Vasp’s POSCAR/CONTCAR  | poscar, contcar    | vasp, poscar, contcar |          | 3D       |
| genFormat             |                    | gen                  | x         | 3D       |
| Gaussian external     |                    | ein                  | x         |          |

For periodic calculations, only the Turbomole, VASP POSCAR/CONTCAR, and genFormat files are supported.
More details on file formats can be found in the [documentation](https://xtb-docs.readthedocs.io/en/latest/geometry.html).

## Calling xtb

The simplest way to start an **xtb** calculation requires only a structure file in one of the supported formats, *e.g.*,

```bash
xtb struc.xyz
```

To perform specific calculations or access different functionalities, you can use various command-line flags when running **xtb**. These flags will be introduced in the following exercises. Many of them can also be combined, allowing you to, for example, perform a geometry optimization with an implicit solvent model.

## Charges and Unpaired Electrons
**xtb**  supports charged molecules as well as molecules with unpaired electrons. You can define charges and the number of unpaired electrons either via command-line flags (`--chrg <INT>` and `--uhf <INT>`) or by placing a *.CHRG* or *.UHF* file in the working directory, each containing only the respective value.
{% include note.html content='Be aware that in **xtb**, you provide the number of unpaired electrons, not the multiplicits as in other QM codes.'%}


## Available Methods
**xtb** supports the GFN2-xTB, GFN1-xTB, and GFN-FF methods. By default, GFN2-xTB is used. Other methods can be employed by providing the corresponding flag:

```bash
xtb struc.xyz --gfn2
xtb struc.xyz --gfn1
xtb struc.xyz --gfnff
```

## Additional Input File
While **xtb** has robust default settings, you may need to adjust parameters for certain calculations.
This can be done by providing an additional input file:

```bash
xtb struc.xyz --input <xtb.inp>
```

These input files can contain multiple blocks, each beginning with a keyword (*e.g.*, `$md`), followed by various settings, and ending with `$end`. For instance, to set the time and temperature for a molecular dynamics (MD) simulation, you can use the following input file:

```bash
$md
   time=10 #ps
   temp=200 #K
$end
```

More detailed settings will be explained in the respective exercises.

## Constraining and Fixing Structures
The additional input file also allows you to constrain specific bonds and angles
This is very important when you want to maintain certain bonding motifs during optimization or MD simulations. A constraint block might look like this:

```bash
$constrain
   distance: 1, 2, 1.4
   angle: 5, 7, 8, auto
   dihedral: 3, 4, 1, 7, 180
$end
```

Here:
* The distance of atoms 1 and 2 in the input file is constrained to 1.4 Angsröm.
* The angle between atom 5,7, and 8 is constrained to the current angle (due to the `auto` keyword).
* The dihedral angle between the atoms 1, 3, 4, and 7 is constrained to 180°.

You can also constrain atoms relative to each other using the `atoms:` keyword (for specific atom indices) or the `elements:` keyword (for all atoms of a given element). For example:

```bash
$constrain
   atoms: 11,12,1-3
   elements: C,N
$end
```

This constrains atoms 1, 2, 3, 11, and 12 relative to each other, as well as all carbon and nitrogen atoms.
If constraints are not sufficient, you can use the $fix block with the `atoms:` or `elements:` keywords to completely fix atomic positions in Cartesian space.
However, this only applies to geometry optimizations and does not work for MD simulations. More details can be found in the [documentation](https://xtb-docs.readthedocs.io/en/latest/xcontrol.html).

## Restarting a **xtb** calculation

For every calculation, a `xtbrestart` file is written. When this file is in the directory when starting a new **xtb** calculation, it will automatically be read and **xtb** tries to use the information to restart a calculation, *e.g.*, a converged Wavefunction.
