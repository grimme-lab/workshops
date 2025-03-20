---
layout: default
title: Frequencies
parent: "xtb"
nav_order: 6
has_children: false
permalink: page/xtb/Frequencies
---

# Frequency calculations

With **xtb**, you can also perform Hessian calculations, which are required for thermocorrections to free energies and for computing IR and Raman spectra. To run a Hessian calculation, use the `--hess` flag.  

```bash
xtb struc.xyz --hess
```

Alternatively, the `--ohess` flag can be used to directly perform an optimization followed by a Hessian calculation.  

{% include warning.html content='Computing Hessians on structures that are not fully optimized will have no physical meaning. This should generally be avoided when computing thermocontributions or spectra.'%}  

At the end of the calculation, the output will include the frequencies, total free energy, and the total thermocorrection (`G(RRHO) contrib.`) at the chosen temperature (default 298.15 K):

```bash
         :::::::::::::::::::::::::::::::::::::::::::::::::::::
         ::                  THERMODYNAMIC                  ::
         :::::::::::::::::::::::::::::::::::::::::::::::::::::
         :: total free energy         -97.955199823991 Eh   ::
         ::.................................................::
         :: total energy              -98.337562149475 Eh   ::
         :: zero point energy           0.443793453483 Eh   ::
         :: G(RRHO) w/o ZPVE           -0.061431127998 Eh   ::
         :: G(RRHO) contrib.            0.382362325484 Eh   ::
         :::::::::::::::::::::::::::::::::::::::::::::::::::::
```

To adjust the temperature, an additional input file can be provided. Even multiple temperatures are possible, *e.g.*:

```bash
$thermo
    temp=150.0,200.0,250.0,273.15,298.15
$end
```

Additionally, a `vibspectrum` file will be generated, containing the IR-active modes with their respective intensities. A Gaussian output file (`g98.out`) will also be created, which can be opened with tools like **Molden** to directly view the vibrational levels.
{% include tip.html content='By activating the `Norm. Mode` in the top right of the Molden control window, a list of frequencies is shown that can be selected to display the respective vibrational mode.'%}  

These vibrational levels can be used to identify transition states or to confirm that the geometry has converged to a minimum.  

## Exercise

Assess the provided structure and check whether it represents a minimum, a reasonable transition state, or an arbitrary point on the potential energy surface (PES).
Use GFN2-xTB with ALPB(THF).
Observe how the spectrum changes when switching to GFN-FF with ALPB(THF) instead.  

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

Ir 0.22444 0.14527 -0.19941
B 1.33274 -1.02240 1.19281
O 2.10728 -0.52368 2.23124
O 1.29878 -2.41761 1.23252
C 2.75593 -1.61003 2.89859
C 2.04814 -2.87405 2.36426
B 1.80738 -0.67323 -1.25750
O 1.60340 -1.37252 -2.45859
O 3.15353 -0.70050 -0.91729
C 2.83363 -1.99118 -2.85163
C 3.89810 -1.30030 -1.97774
B 1.44948 1.70801 0.27916
O 2.50688 2.19680 -0.48225
O 1.26386 2.52815 1.40609
C 3.16792 3.23950 0.23108
C 2.18823 3.61911 1.36048
C -2.30905 -0.65090 1.42723
C -2.25834 -1.68944 0.37026
N -1.30803 0.26358 1.43328
N -1.23625 -1.60021 -0.50919
C -3.32614 -0.60417 2.38997
C -3.30852 0.38423 3.36785
C -2.26730 1.30909 3.36702
C -1.28713 1.21455 2.38323
C -3.20068 -2.72376 0.27943
C -3.08457 -3.67137 -0.73143
C -2.02500 -3.56877 -1.63030
C -1.12272 -2.51872 -1.48063
C -1.14523 1.44405 -1.40055
C -1.32790 2.78803 -1.02925
C -1.99683 0.92863 -2.39248
C -2.34780 3.56470 -1.58615
C -3.01467 1.70232 -2.95766
C -3.19935 3.02499 -2.55218
H 0.37405 0.80500 -1.68399
H -0.44935 1.90106 2.33342
H -2.20575 2.09631 4.11121
H -4.09485 0.42683 4.11592
H -4.12897 -1.33084 2.37621
H -4.01648 -2.79488 0.98859
H -3.80980 -4.47600 -0.81155
H -1.89129 -4.28555 -2.43403
H -0.27298 -2.38745 -2.14226
H 1.35904 -3.30922 3.10064
H 2.74940 -3.65517 2.05006
H 2.65464 -1.48884 3.98290
H 3.82436 -1.59665 2.64805
H 1.64159 4.54652 1.14131
H 2.67739 3.72788 2.33451
H 3.38162 4.07382 -0.44625
H 4.12089 2.86119 0.62441
H 4.43772 -0.51679 -2.52565
H 4.63150 -2.00027 -1.56306
H 2.99198 -1.84055 -3.92463
H 2.77505 -3.07061 -2.65637
H -0.67931 3.23230 -0.27913
H -2.47374 4.59719 -1.26591
H -3.98804 3.63103 -2.99159
H -3.65923 1.27131 -3.72132
H -1.86324 -0.09332 -2.73789
{% endcapture %}
{% include codecell.html content=struc_file_1 style="font-size:10px" %}
</div>

## Single-Point Hessian

Another feature of **xtb** is the Single-Point Hessian (SPH) approach, which allows the calculation of reasonable Hessians on arbitrary structures.  

This can be useful, for example, to compute thermocorrections for a DFT-optimized structure, saving computational time compared to a more expensive DFT Hessian calculation.  

To activate the SPH approach, use the `--bhess` flag, *e.g.*

```bash
xtb struc.xyz --bhess
```

{% include warning.html content='SPH is often not suitable for transition states, as the imaginary mode will also be lost.'%}

For further details, please refer to the [documentation](https://xtb-docs.readthedocs.io/en/latest/hessian.html#single-point-hessian-sph-calculations) and the [publication](https://pubs.acs.org/doi/10.1021/acs.jctc.0c01306).  
