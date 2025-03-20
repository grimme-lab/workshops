---
layout: default
title: Periodic Calculations
parent: "xtb"
nav_order: 12
has_children: false
permalink: page/xtb/periodic
---

# Periodic Calculations

Starting from **xtb** version 6.7.0, the GFN-FF method supports periodic calculations using periodic boundary conditions. Additionally, a special run mode called mcGFN-FF, which includes scaled non-covalent interactions (NCI), was introduced and is recommended for periodic systems. This mode can be used for a fast optimization of periodic systems, optionally without optimizing the cell parameters (*--nocellopt*).

A periodic GFN-FF calculation is invoked similarly to a normal GFN-FF calculation, with the exception that the structure input file must contain lattice information. Therefore, only the Turbomole, Vasp’s POSCAR/CONTCAR, and genFormat file formats are supported.

{% include note.html content='With **xtb**, only GFN-FF is available for periodic calculations and no Hessian computation is possible. However, in [DFTB+](https://www.dftbplus.org/), a periodic implementation of the GFN-xTB methods is available.' %}

To perform a periodic optimization with mcGFN-FF, use the following command:


```bash
xtb struc.coord --mcgfnff --opt
```

The resulting structure can be found in the `xtbopt.coord` file, which includes the optimized lattice parameters. A trajectory of the optimization is available in the `xtboptlog.cif` file.

## Exercise

As an example, optimize the unit cell of benzene. To visualize the structure, you can convert the Turbomole format to xyz using a tool like **mctc-convert** and then open it with a graphical program such as Molden.

<!-- Tab links -->
<div class="tab card">
  <button
    class="tablinks tab-id-1"
    onclick="openTabId(event, 'struc-1', 'tab-id-1')"
    id="open-1">
    {{ site.data.icons.codefile }} <code>benzene.xyz</code>
  </button>
</div>
<!-- Tab content -->
<div id="struc-1" class="tabcontent tab-id-1" style="text-align:justify">
{% capture struc_file_1 %}
$coord
    7.10986726811546E+00    1.39803317039751E+01    9.79695027924021E+00      C
    7.11375821259805E+00    8.76795203096078E+00    3.36407395831929E+00      C
    8.60482372324771E+00    5.13823133707231E+00    1.25907033747429E+01      C
    9.75112376027930E+00    7.53368379774428E+00    1.25988946977277E+01      C
    5.96704128865761E+00    6.37267695865231E+00    3.35549866706958E+00      C
    9.00267279659253E+00    9.34854414468852E+00    1.58886068020756E+00      C
    6.71563121464733E+00    4.55781661170807E+00    1.56671851026428E+00      C
    2.01592612889045E+00    1.34582777502016E+01    1.56454269009644E+00      C
    1.36276161633625E+01    5.11410651963663E-01    1.59001258500230E+00      C
    2.76479397948607E+00    1.52711868251473E+01    3.35524268822630E+00      C
    1.28790262373728E+01    1.64375153151443E+01    1.25977427929330E+01      C
    1.62071733930167E+00    5.14124693925177E+00    9.79797419461331E+00      C
    1.27150507198922E-01    8.76741986587029E+00    6.22310165885711E+00      C
    2.76687841403031E+00    7.53687678828724E+00    9.78696710435249E+00      C
    1.28772197274344E+01    6.37179001683482E+00    6.23423673853957E+00      C
    2.01689886501110E+00    9.34978586323301E+00    7.99677906390919E+00      C
    1.27706356410721E-01    1.40413533010183E+01    1.25881435863102E+01      C
    1.61946667857512E+00    1.76671714509098E+01    3.36548184195730E+00      C
    8.99919873901879E+00    1.33969013764314E+01    8.02314488476650E+00      C
    5.96523477871927E+00    1.63766711064646E+01    9.78632715724430E+00      C
    9.74959517494686E+00    1.52094556746502E+01    6.23270086547992E+00      C
    8.60482372324771E+00    1.76057950771396E+01    6.22182176464074E+00      C
    6.71535329004143E+00    4.50389054920479E-01    7.99562715911445E+00      C
    1.36270603141507E+01    4.55888094188905E+00    8.02442477898288E+00      C
    1.12337125704490E+01    7.97130089049293E+00    1.12071377268419E+01      H
    5.79806312827085E+00    2.31828852255051E+00    7.97514885165245E+00      H
    9.14344160948052E+00    3.72249480799774E+00    1.11681009532424E+01      H
    6.57555721327409E+00    1.01835111716719E+01    4.78718833750633E+00      H
    4.24696590274695E+00    1.48321506254907E+01    4.74712764853380E+00      H
    1.27099091146831E+01    2.37913273123019E+00    1.60972295593447E+00      H
    2.93391110217578E+00    1.15907330592985E+01    1.54457634032100E+00      H
    1.13967153518090E+01    1.68763741264374E+01    1.12061138114688E+01      H
    4.48473040309378E+00    5.93505986590366E+00    4.74751161679871E+00      H
    2.15975211244333E+00    3.72728429381217E+00    1.12222404785951E+01      H
    5.79667350524135E+00    2.69080408589553E+00    1.54803205470521E+00      H
    9.92149154369556E+00    1.12155566705011E+01    1.60729115692336E+00      H
    1.34851798028391E+01    1.26270358788517E+01    1.11638773023284E+01      H
    1.13944919549618E+01    5.93293120554168E+00    4.84311971476190E+00      H
    4.25002307341184E+00    7.97555821121688E+00    1.11778281492869E+01      H
    1.27082415670477E+01    2.69186841607651E+00    8.04490308644487E+00      H
    2.93557864981118E+00    1.12169757774090E+01    7.97591678818228E+00      H
    6.56985975885316E+00    1.25663690585355E+01    1.12210885738004E+01      H
    9.14510915711592E+00    1.28092137281638E+00    4.79793944892387E+00      H
    1.12321839851166E+01    1.47700646982665E+01    4.84171183112389E+00      H
    4.48153427012594E+00    1.68157073061212E+01    1.11765482550705E+01      H
    9.91718371230412E+00    1.15293566855284E+01    8.04375118165014E+00      H
    1.34839291421126E+01    1.01815598996734E+01    4.79909135371861E+00      H
    2.15794560250498E+00    1.34247513495005E+00    4.79000410478235E+00      H
$periodic 3
$lattice bohr
    13.89623029496416    0.00000000000000    0.00000000000000
     0.00000000000000   17.73883634976286    0.00000000000000
     0.00000000000000    0.00000000000000   12.79894216374709
$end
{% endcapture %}
{% include codecell.html content=struc_file_1 style="font-size:10px" %}
</div>
