---
layout: default
title: SP
full_title: Single-Point Calculation
parent: "xtb"
nav_order: 3
has_children: false
permalink: page/xtb/sp
---

# Single-Point Calculations  

The most fundamental feature of **xtb** is computing electronic energies. This calculation is performed automatically every time an **xtb** run is initiated.  
You can explicitly request a single-point calculation using:  

```bash
xtb struc.xyz --sp
```

The electronic energy, given in Hartree, is printed at the end of the output as `TOTAL ENERGY`, along with the `GRADIENT NORM` and the `HOMO-LUMO GAP`.  

Single-point calculations in **xtb** can be useful for quickly identifying reasonable conformers. For example, you can determine the lowest-energy gas-phase conformer by comparing electronic energies.

## Exercise

As an exercise, identify the lowest-energy conformer for the following two structures using both GFN-FF and GFN2-xTB. Then, compute their energy difference in kcal/mol.  

{% include note.html content='1 Hartree = 627.503 kcal/mol.'%}

<!-- Tab links -->
<div class="tab card">
  <button
    class="tablinks tab-id-1"
    onclick="openTabId(event, 'struc-1', 'tab-id-1')"
    id="open-1">
    {{ site.data.icons.codefile }} <code>conf1.xyz</code>
  </button>
  <button
    class="tablinks tab-id-1"
    onclick="openTabId(event, 'struc-2', 'tab-id-1')">
    {{ site.data.icons.codefile }} <code>conf2.xyz</code>
  </button>
</div>
<!-- Tab content -->
<div id="struc-1" class="tabcontent tab-id-1" style="text-align:justify">
{% capture struc_file_1 %}
40
Energy =
O     2.8656865    0.5086790    1.3197062 
C     2.9608465    1.3781190    0.4782162 
O     3.9258365    2.3120790    0.4899462 
H     4.4705065    2.1269290    1.2702563 
C     2.0089165    1.5718490   -0.6774237 
C     1.2218365    2.8726290   -0.5104438 
H     0.5452365    2.9727090   -1.3548738 
H     0.6374265    2.8387490    0.4080463 
H     1.8941065    3.7273190   -0.4842237 
H     2.5858265    1.6221090   -1.6024638 
N     1.1570565    0.4147690   -0.7077437 
H     1.1682765   -0.1851510    0.1004562 
C     0.4547365    0.0498590   -1.8004238 
O     0.4143565    0.7088490   -2.8348837 
C    -0.3359535   -1.2532710   -1.6476638 
H    -0.0269735   -1.8943310   -2.4724237 
N    -0.0439735   -1.9464710   -0.4179737 
H    -0.4437335   -1.6251410    0.4556562 
C     1.0449065   -2.7567710   -0.3028238 
O     1.7205465   -3.1364810   -1.2489437 
C     1.3476865   -3.1714810    1.1313163 
H     2.4156765   -3.3901810    1.1668263 
H     0.8153865   -4.1048210    1.3166462 
N     0.8864165   -2.1654010    2.0880563 
H     0.7812065   -2.5725610    3.0070963 
H     1.5766565   -1.4271210    2.1744762 
C    -1.8356235   -0.9421110   -1.7606137 
H    -1.9948435   -0.4470910   -2.7176738 
H    -2.3823335   -1.8853110   -1.7612237 
C    -2.2945635   -0.0653810   -0.6306337 
C    -2.1976335    1.3274490   -0.7299938 
H    -1.8465635    1.7652190   -1.6561638 
C    -2.5483335    2.1427590    0.3430863 
H    -2.4749535    3.2179390    0.2471862 
C    -2.9994235    1.5773690    1.5353163 
H    -3.2729535    2.2106090    2.3681563 
C    -3.1088535    0.1928090    1.6437062 
H    -3.4691135   -0.2535310    2.5606562 
C    -2.7612435   -0.6201710    0.5658963 
H    -2.8620635   -1.6960210    0.6479063 
{% endcapture %}
{% include codecell.html content=struc_file_1 style="font-size:10px" %}
</div>
<div id="struc-2" class="tabcontent tab-id-1" style="text-align:justify">
{% capture struc_file_2 %}
40
Energy =
O    -0.7784810    0.9576770    5.7268255 
C    -0.9737110    0.2611170    4.7601655 
O    -2.2037210   -0.1090930    4.3828155 
H    -2.1370810   -0.6604030    3.5681155 
C     0.1586390   -0.2846530    3.8806455 
C     1.5146990    0.1371970    4.4029555 
H     2.3036390   -0.2844730    3.7831355 
H     1.5969990    1.2219670    4.4013155 
H     1.6411190   -0.2009830    5.4270155 
H     0.0646390   -1.3746330    3.8792655 
N     0.0108590    0.1662570    2.5005855 
H     0.7060590    0.7969570    2.1009255 
C    -0.8578710   -0.3970130    1.6490855 
O    -1.7221410   -1.2152430    1.9931455 
C    -0.6966010    0.0606870    0.2003455 
H    -0.6989610    1.1548170    0.1998355 
N     0.5849790   -0.3575730   -0.3352345 
H     0.6392690   -1.0698530   -1.0538745 
C     1.7056390    0.3670370   -0.1649545 
O     1.8033390    1.3083670    0.6275255 
C     2.8738890   -0.0710330   -1.0300845 
H     3.5601090   -0.6186530   -0.3843745 
H     3.3852490    0.8427970   -1.3386345 
N     2.4434290   -0.9468530   -2.1165445 
H     3.2259990   -1.4733230   -2.4795245 
H     2.0704490   -0.4026530   -2.8854245 
C    -1.8214910   -0.4657430   -0.6848745 
H    -1.8713110   -1.5502830   -0.5862745 
H    -2.7651510   -0.0718430   -0.3085445 
C    -1.5891810   -0.0664830   -2.1143745 
C    -1.1455410   -0.9995930   -3.0548145 
H    -1.0385310   -2.0377230   -2.7632045 
C    -0.8512410   -0.6142830   -4.3622745 
H    -0.5161810   -1.3521630   -5.0788045 
C    -0.9972910    0.7172970   -4.7447145 
H    -0.7733810    1.0197170   -5.7584145 
C    -1.4472710    1.6567670   -3.8169645 
H    -1.5731910    2.6901770   -4.1098845 
C    -1.7396210    1.2655270   -2.5133545 
H    -2.0910510    2.0001870   -1.7985545 
{% endcapture %}
{% include codecell.html content=struc_file_2 style="font-size:10px" %}
</div>
{% include defaulttab.html id="open-2" %}

The predicted energy difference between these two conformers, as calculated using CCSD(T), is that conf1 is 1.4 kcal/mol higher in energy than conf2. Are both results reasonable? 

{% include note.html content='GFN-FF and GFN2-xTB may exhibit larger errors in conformational energies for electronically complex systems and might even fail to identify the lowest-energy conformer. In such cases, DFT refinement with methods like **CENSO** is recommended for more reliable predictions.  

A way to improve the performance of GFN-FF for conformer ranking is [ConfRank](https://pubs.acs.org/doi/10.1021/acs.jcim.4c01524).'%}  

## Further Settings

For the energy calculations, **xtb** tries to converge the atomic charges of the molecule, which is equal to converging a Wavefunction. The behaviour of this self-consistent charge (SCC) convergence can be adjusted, *e.g.*, the `--acc <REAL>` flag changes the accuracy and the `--iterations <INTEGER>` lets you change the maximum number of SCC cycles. The latter is particularly useful when the wavefunction does not converge within the default 250 cycles, which may occur in very large or electronically complex systems.  

However, if converging the Wavefunction fails, it should first be checked manually before increasing the number of iterations, as some systems may not converge at all.

More details on adjusting convergence parameters can be found in the [xtb manual](https://xtb-docs.readthedocs.io/en/latest/sp.html#accuracy-and-iterations).  
