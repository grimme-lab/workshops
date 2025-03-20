---
layout: default
title: Ensemble Generation
parent: "CREST"
nav_order: 3
has_children: false
permalink: page/crest/ensemble
---

# {{ page.title }}

The main feature of **crest** is the generation of an ensemble and the search for the global minimum of a structure. This can be done with the following command:

```bash
crest struc.xyz
```

This results in a file called `crest_best.xyz` containing the best conformer found, `crest_conformers.xyz` containing the conformer ensemble sorted by energy and without duplicates, and the `crest_rotamers.xyz` file containing an ensemble of rotamers sorted by energy.

Many features of **xtb** can be used also with **crest**, for example, implicit solvation and the different GFN methods. The command line flags are similar to **xtb**, *e.g.,* `--alpb <solvent>` or `--gfnff`.  
You can define the number of cores to use with the **-T <Int>** argument. All available flags are listed in the [documentation](https://crest-lab.github.io/crest-docs/page/documentation/keywords.html).

**crest** comes with mostly robust defaults. However, setting robust defaults covering the complete chemical space is not possible. Therefore, it might be necessary to adjust these defaults like the MD length (`--mdlen <REAL>`).
To get a feeling on whether the settings are reasonable, the `--keepdir` flag can be used when starting a crest run. This will leave a `MDFILES` folder with different trajectories of the **crest** runs.
Inspecting them with, *e.g.*, Molden can be used to check how the molecule behaves during the simulations.
More on this is explained in the [respective chapter](page/crest/nci).

{% include warning.html content='Per default, **crest** generates an ensemble with structures in a certain energy window, *e.g.*, for a conformer search 6 kcal/mol. Every conformer above this window will be discarded and is lost forever. Especially for electronically challenging systems, where the applied method, *e.g.*, GFN2-xTB, is expected to have larger errors, important conformers are lost and cannot be recovered by following ensemble refinements. Thus, it is very important to increase the energy window for such cases with the `--ewin <REAL>` flag.' %}

## Exercise

As a simple example, compute the ensemble of histidine including implicit water solvation with the GFN-FF method.

<!-- Tab links -->
<div class="tab card">
  <button
    class="tablinks tab-id-1"
    onclick="openTabId(event, 'struc-1', 'tab-id-1')"
    id="open-1">
    {{ site.data.icons.codefile }} <code>histidine.xyz</code>
  </button>
</div>
<!-- Tab content -->
<div id="struc-1" class="tabcontent tab-id-1" style="text-align:justify">
{% capture struc_file_1 %}
20

O     -1.0689000000   -1.6919000000   -0.7660000000
O     -2.4946000000   -1.1223000000    0.9038000000
N      1.6797000000    0.1409000000    1.1624000000
N     -2.7494000000    1.3693000000   -0.2178000000
N      2.8201000000   -0.3365000000   -0.6825000000
C     -0.3579000000    1.3004000000    0.3217000000
C     -1.5062000000    0.6397000000   -0.4567000000
C      0.9671000000    0.6020000000    0.1195000000
C     -1.7498000000   -0.7917000000   -0.0102000000
C      1.6556000000    0.3150000000   -1.0031000000
C      2.8043000000   -0.4249000000    0.6290000000
H     -0.5942000000    1.3196000000    1.3946000000
H     -0.2433000000    2.3450000000    0.0039000000
H     -1.3124000000    0.6416000000   -1.5355000000
H      1.4441000000    0.1943000000    2.1450000000
H      1.3992000000    0.5299000000   -2.0301000000
H     -2.6419000000    2.3346000000   -0.5280000000
H     -2.9358000000    1.4198000000    0.7835000000
H      3.5655000000   -0.8810000000    1.2458000000
H     -1.2415000000   -2.6142000000   -0.4801000000
{% endcapture %}
{% include codecell.html content=struc_file_1 style="font-size:10px" %}
</div>

After the CREST calculation, you will find an ensemble and some additional files in your working directory. The ensemble will be dumped in XYZ format in a file called `crest_conformers.xyz`. You can have a look at the ensemble file by opening it with, *e.g.*, molden.

{% include warning.html content='CREST works stochastically and is thus non-deterministic. For molecules with higher flexibility, the results of CREST might differ and multiple runs should be used.' %}
