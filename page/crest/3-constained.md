---
layout: default
title: Constraints
parent: "CREST"
nav_order: 5
has_children: false
permalink: page/crest/constraints
---

# Constraints

For electronically more complex systems, such as transition metal complexes, or if you wish to preserve specific structural motifs (*e.g.*, a transition state), **crest** offers the option to constrain certain bonds, dihedrals, and torsion angles. 

To do this, you can provide a file with a format similar to the [**xtb** input](page/xtb/general#constraining-and-fixing-structures) using the **--cinp** flag:

```bash
crest struc.xyz --cinp <FILE> --subrmsd
```

The `--subrmsd` flag causes **crest** to compare only those parts of the structure that were also included in the metadynamics bias potential.

All possible constraints are listed in the [documentation](https://xtb-docs.readthedocs.io/en/latest/xcontrol.html#fixing-constraining-and-confining).

{% include note.html content='Exact atom fixing is not possible due to instabilities during MD and MTD simulations.' %}

To simplify the manual definition of constraints, **crest** offers the option to automatically generate the required input file.
For this, the `--constrain <atomlist>` keyword can be used, where `<atomlist>` defines the indices of the atoms to be constrained, *e.g.*:

```bash
crest struc.xyz --constrain 1-5,8,12
```

This results in a `.xcontrol.sample` file, which can be renamed and used as input for the **crest** run as well as a `coord.ref` file used as reference for the constraining. 

Additionally, **crest** provides the option to automatically constrain certain interaction motifs. For example, **--cmetal** constrains the bonds between a metal and all ligands to prevent unwanted behavior during MD and MTD simulations. More information can be found in the [documentation](https://crest-lab.github.io/crest-docs/page/examples/example_4.html).

## Exercise

As an example, consider the transition state of the oxidative addition of benzene to an Ir catalyst.
Search for conformers of the transition state with GFN-FF in THF by constraining the relevant atoms. 
To do this, examine the structure using software like Molden, display the labels and atom numbers, and take note of the atom numbers of atoms relevant for the transition state (you can also identify by performing a **xtb** frequency calculation and checking the imaginary frequency).
Then, call **crest** with the `--constrain <atomlist>` flag, replacing `<atomlist>` with the appropriate atom numbers.
Rename the resulting `.xcontrol.sample` file to a name of your choice, such as `xtb.inp`, and start **crest** again, providing this input file. 
As this is a electronically more complex molecule, increase the energy window to 30 kcal/mol (`--ewin 30`).
Finally, verify that `crest_best.xyz` represents a reasonable transition state, similar to what was shown [before](page/xtb/Frequencies).

<!-- Tab links -->
<div class="tab card">
  <button
    class="tablinks tab-id-1"
    onclick="openTabId(event, 'struc-1', 'tab-id-1')"
    id="open-1">
    {{ site.data.icons.codefile }} <code>struc.xyz</code>
  </button>
</div>
<!-- Tab content -->
<div id="struc-1" class="tabcontent tab-id-1" style="text-align:justify">
{% capture struc_file_1 %}
   60
FINAL HEAT OF FORMATION =   -10.652236
Ir     0.183562     0.007648    -0.034276
 B     1.105603    -1.318961     1.507833
 O     1.750576    -0.765030     2.609861
 O     1.056026    -2.707974     1.409728
 C     2.218956    -1.890502     3.322169
 C     1.760197    -3.147882     2.551868
 B     1.830913    -0.804148    -1.261756
 O     1.569192    -0.985666    -2.621398
 O     3.102286    -1.126315    -0.790834
 C     2.786325    -1.492861    -3.123711
 C     3.796277    -1.516005    -1.956777
 B     1.356214     1.835824     0.243472
 O     2.297869     2.181902    -0.725072
 O     1.160116     2.714197     1.313025
 C     2.831475     3.397478    -0.243161
 C     2.109970     3.731991     1.079859
 C    -2.187317    -0.733022     1.465202
 C    -2.128710    -1.676766     0.343637
 N    -1.207227     0.200038     1.549249
 N    -1.094669    -1.556386    -0.527617
 C    -3.178877    -0.732774     2.438232
 C    -3.143042     0.198364     3.452403
 C    -2.124571     1.130718     3.501850
 C    -1.158193     1.111240     2.528940
 C    -3.069231    -2.673918     0.114600
 C    -2.933610    -3.508373    -0.972445
 C    -1.862043    -3.358253    -1.831075
 C    -0.945976    -2.368038    -1.583761
 C    -1.159801     1.404740    -1.125045
 C    -1.105228     2.754179    -0.875819
 C    -2.068280     0.907573    -2.026386
 C    -1.949133     3.618338    -1.544122
 C    -2.915488     1.762955    -2.702242
 C    -2.853341     3.121896    -2.461411
 H     0.313687     0.668710    -1.526625
 H    -0.349040     1.820852     2.518451
 H    -2.089589     1.864410     4.290756
 H    -3.910826     0.200329     4.209757
 H    -3.971000    -1.459019     2.401558
 H    -3.903732    -2.792065     0.782309
 H    -3.663763    -4.281399    -1.153805
 H    -1.746239    -4.007743    -2.683587
 H    -0.098647    -2.209801    -2.227424
 H     1.086337    -3.781560     3.144643
 H     2.603808    -3.765459     2.213226
 H     1.806418    -1.846429     4.338517
 H     3.312104    -1.815563     3.390209
 H     1.581634     4.693743     1.040438
 H     2.796937     3.752779     1.936209
 H     2.672051     4.165503    -1.012870
 H     3.914153     3.265315    -0.109524
 H     4.621871    -0.807232    -2.106982
 H     4.225315    -2.512403    -1.787757
 H     3.110396    -0.849172    -3.952446
 H     2.592694    -2.496512    -3.524796
 H    -0.400619     3.123541    -0.151170
 H    -1.901896     4.677345    -1.349469
 H    -3.513811     3.794581    -2.985626
 H    -3.625714     1.370496    -3.411901
 H    -2.119903    -0.155991    -2.183099
{% endcapture %}
{% include codecell.html content=struc_file_1 style="font-size:10px" %}
</div>

Please note that GFN-FF and GFN2-xTB are not reliable enough to predict accurate conformational ranking for such a system.
For production runs, the ensemble has to be refined with DFT.
