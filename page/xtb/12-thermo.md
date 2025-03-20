---
layout: default
title: Thermo Submodule
parent: "xtb"
nav_order: 13
has_children: false
permalink: page/xtb/thermo
---

# Thermodynamic Corrections

With the **xtb** thermo submodule, thermodynamic properties of a structure can be evaluated based on a previously calculated Hessian. The mRRHO approximation is used for these calculations. It can be invoked with:

```bash
xtb thermo [options] struc.xyz <hessian file>
```

With [options], the type of Hessian is defined, **e.g.**, **--orca** or **--turbomole**.
The output will display a `total energy` of 0 Hartree, with the sum of thermocorrections as `total free energy`, and include different components such as `zero point energy`, `G(RRHO) w/o ZPVE`, and `G(RRHO) contrib.`:

```bash
         :::::::::::::::::::::::::::::::::::::::::::::::::::::
         ::                  THERMODYNAMIC                  ::
         :::::::::::::::::::::::::::::::::::::::::::::::::::::
         :: total free energy           0.743903967832 Eh   ::
         ::.................................................::
         :: total energy                0.000000000000 Eh   ::
         :: zero point energy           0.826262177517 Eh   ::
         :: G(RRHO) w/o ZPVE           -0.082358209684 Eh   ::
         :: G(RRHO) contrib.            0.743903967832 Eh   ::
         :::::::::::::::::::::::::::::::::::::::::::::::::::::
```

The thermo submodule is especially useful, when evaluating different temperatures.
The temperature can be set with the `--temp <REAL>` flag.
For further details, refer to the [documentation](https://xtb-docs.readthedocs.io/en/latest/xtb_thermo.html).
