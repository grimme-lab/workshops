---
layout: default
title: Docking
parent: "xtb"
nav_order: 13
has_children: false
permalink: page/xtb/docking
---

# Docking

Another feature of the **xtb** program is the *aISS* docking tool. This efficient tool is designed for docking two or more molecules. It can be used with:


```bash
xtb dock mol1.xyz mol2.xyz
```

The best structure found is saved to `best.xyz`. Additionally, by default, the 15 best structures are written to the `final_structures.xyz` file. Both files can be visualized by opening them with a graphical program like Molden.
The `best_after_gen.xyz` file contains the best structure found before GFN optimization.

Charges and the number of unpaired electrons for both molecules can be defined individually using the `--chrg1 <INT>`, `--chrg2 <INT>`, `--uhf1 <INT>`, and `--uhf2 <INT>` flags.
Many standard **xtb** flags like the use of solvation as well as choosing different methods can be applied.
Further, thresholds for the docking can be adjusted with an additional input file. Also, the generation of a whole ensemble with the `--ensemble` flag can be requested. Further details are available at the [documentation](https://xtb-docs.readthedocs.io/en/latest/xtb_docking.html) and the [publication](https://onlinelibrary.wiley.com/doi/full/10.1002/anie.202214477).

{% include warning.html content='Due to technical issues, docking in xtb version 6.7.1 may not work properly. It is recommended to use version 6.7.0 or a bleeding-edge version of xtb for this exercise.' %}

As an example, dock the following molecules in THF solvent. Molecule 1 has a charge of +1, while molecule 2 has a charge of -1.

{% include note.html content='The calculation can be speed up by using the `--fast` flag.' %}

<!-- Tab links -->
<div class="tab card">
  <button
    class="tablinks tab-id-1"
    onclick="openTabId(event, 'struc-1', 'tab-id-1')"
    id="open-1">
    {{ site.data.icons.codefile }} <code>mol1.xyz</code>
  </button>
  <button
    class="tablinks tab-id-1"
    onclick="openTabId(event, 'struc-2', 'tab-id-1')">
    {{ site.data.icons.codefile }} <code>mol2.xyz</code>
  </button>
</div>
<!-- Tab content -->
<div id="struc-1" class="tabcontent tab-id-1" style="text-align:justify">
{% capture struc_file_1 %}
26
 energy: -48.614767811026 gnorm: 0.000258649455 xtb: 6.4.1 (afa7bdf)
C         4.91530661517725    6.70283245094063    7.93716475951803
C         4.70274443502525    6.57377729590493    9.29524339877115
H         4.09102174399250    7.26033628697812    9.85619438676986
C         5.30083332347772    5.50886296651214    9.95148435215316
H         5.14950194396918    5.39341270236785   11.01271420108665
C         6.07968625421465    4.60874288641406    9.24518865717228
H         6.54677504050510    3.78278315133684    9.75767540823253
C         6.25703022783366    4.75482454682128    7.88004220926858
H         6.86007029320169    4.04168399010195    7.34301476032045
C         5.66602589617880    5.80800301477451    7.18908033030661
C         5.86757693738733    6.01057612526783    5.69193856008651
C         7.08202831053878    6.91791330345741    5.48228665306979
H         7.24115049352935    7.07340643740184    4.41937035609539
H         7.97015992903950    6.46898272395727    5.91528468405366
H         6.90905459937370    7.88538694516834    5.94891470399975
C         6.00723529207749    4.69862546864148    4.92713759447965
H         5.21841097621933    3.99954166143467    5.19740910959166
H         6.96848369282735    4.23481873803338    5.12168284991214
H         5.95419366234075    4.90262716196177    3.86004767791694
C         3.64840129849507    9.67356063984810    8.63166910176501
O         4.73243266730302    6.72691667725402    5.16545009366973
H         4.06891690953035    6.10561213656021    4.82852948175645
F         4.75466800938595    9.73439880907246    9.35215456436095
F         2.67459899148865    9.19239065754443    9.38100275774183
F         3.32953186458964   10.86751693409879    8.19537197705647
I         4.01066059229276    8.37336628814393    6.88654737084331
{% endcapture %}
{% include codecell.html content=struc_file_1 style="font-size:10px" %}
</div>
<div id="struc-2" class="tabcontent tab-id-1" style="text-align:justify">
{% capture struc_file_2 %}
15
 energy: -58.627917250038 gnorm: 0.000569925187 xtb: 6.4.1 (afa7bdf)
C         1.69917908436396    3.16419000234708    5.71715609389680
C         2.60797179763240    5.77666501630793    1.55859710223873
N         3.04393410713759    4.87876887895570    4.08766375461315
O         1.71709471089772    5.74460140297995    5.99119818311252
O         0.49329287309353    4.87672637525144    4.06446686790556
O         2.06112121487995    3.28932161619064    2.35293444108821
O         4.39145876797790    4.00283070449141    2.20140862554339
F         2.78451881723356    3.06550089656539    6.49714305953822
F         0.63418103893843    3.02555503292592    6.52249893622828
F         1.70857427523024    2.10779486104579    4.90543392667151
F         1.42635733996611    6.33666447079787    1.81496418774220
F         3.53272631929243    6.73443277485248    1.71239388025687
F         2.60933613238697    5.44729166600378    0.25762027938529
S         1.67585920791859    4.85884119332730    4.86637940756559
S         3.05359431305024    4.27861510795718    2.63234125421372
{% endcapture %}
{% include codecell.html content=struc_file_2 style="font-size:10px" %}
</div>
{% include defaulttab.html id="open-2" %}
