---
layout: default
title: NCI
parent: "CREST"
nav_order: 4
has_children: false
permalink: page/crest/nci
---

# NCI Mode

For systems with non-covalently interacting molecules, **crest** provides a special runtype invoked with the **--nci** flag:

```bash
crest struc.xyz --nci
```

This will apply a wall potential to prevent the dissociation of molecules during MTD and MD simulations.

{% include warning.html content='Especially for systems containing non-bonded molecules, conformer generation can be complex, and the results of a single **crest** run are likely insufficient to find the optimal conformer.' %}

For systems with multiple molecules, it is highly recommended to run **crest** multiple times on the same system and combine the results.
You can also sort the combined ensemble using **crest**, as explained in the [additional features chapter](page/crest/addition).
Additionally, it may be helpful to try different settings, such as adjusting the temperature of the MD runs (`--tnmd <INT>`) or increasing the number of search cycles (`--mrest <INT>`).

Adjusting the wall potential to your needs can also become very relevant. This can be done with the `--wscal <REAL>` flag, where `<REAL>` is a scaling of the wall potential size (per default `1.0`).
To see the influence of the wall potential, the `--keepdir` flag can be used to allow checking the trajectories.

{% include note.html content='To generate reasonable starting structures, the [**xtb** docking](page/xtb/docking) can be used.' %}

Further options for tuning the sampling behavior can be found in the [documentation](https://crest-lab.github.io/crest-docs/page/documentation/keywords.html#conformational-search-settings).
