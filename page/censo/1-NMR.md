---
layout: default
title: NMR
parent: "CENSO"
nav_order: 3
has_children: false
permalink: page/censo/nmr
---

# {{ page.title }}

**CENSO** is not only capable of ensemble refinement, but also allows the automated computation of NMR spectra for an entire ensemble. Since NMR is a structure-sensitive property, this is a prime example of the importance of ensemble quality.

## Exercise

{% include note.html content='Due to technical reasons, you are going to use **censo** v1 in the following exercise. However, **censo** 2 is generally advised due to additional features, and updated methods. Please note that the input file structure differs a little, while the principle functionality remains similar. For an overview over the different input file formats, please see the [documentation](https://xtb-docs.readthedocs.io/en/latest/CENSO_docs/censorc.html).'%}

As an example, use **crest** to first generate an ensemble of 2-Fluoropropan-1-ol with GFN2-xTB in water.

<!-- Tab links -->
<div class="tab card">
  <button
    class="tablinks tab-id-1"
    onclick="openTabId(event, 'struc-1', 'tab-id-1')"
    id="open-1">
    {{ site.data.icons.codefile }} <code>2-Fluoropropan-1-ol.xyz</code>
  </button>
</div>
<!-- Tab content -->
<div id="struc-1" class="tabcontent tab-id-1" style="text-align:justify">
{% capture struc_file_1 %}
10

  O     1.398839    1.025407   -0.886750
  C     0.372477    0.456264   -0.628697
  C    -0.032777   -0.054166    0.729167
  H    -0.916315    0.504071    1.066256
  H    -0.386361    0.248155   -1.401738
  C    -0.304030   -1.554058    0.707502
  H    -0.567187   -1.886134    1.707543
  H    -1.123368   -1.765489    0.029484
  H     0.585461   -2.087710    0.383005
  F     0.964760    0.230530    1.658525
{% endcapture %}
{% include codecell.html content=struc_file_1 style="font-size:10px" %}
</div>

{% include important.html content='For the next steps, the ORCA software is required.' %}

Next, you will refine the ensemble using DFT calculations.  
**crest** uses GFN2-xTB as the default method, which produces ensemble rankings that are not accurate enough for, *e.g.*, NMR calculations. Therefore, it is necessary to refine the initial ensemble.  
You can do this using **CENSO**, which automates the process of ensemble refinement.

Use the following input to refine the ensemble.

 <!-- Tab links -->
<div class="tab card">
  <button class="tablinks tab-id-2" onclick="openTabId(event, 'tab-2-1', 'tab-id-2')" id="open-2">{{ site.data.icons.code }} <code>command</code></button>
  <button class="tablinks tab-id-2" onclick="openTabId(event, 'tab-2-2', 'tab-id-2')">{{ site.data.icons.codefile }} <code>censorc</code></button>
</div>
<!-- Tab content -->
<div id="tab-2-1" class="tabcontent tab-id-2" style="text-align:justify">
{% include command.html cmd="censo -inp crest_conformers.xyz -inprc censorc -T 8 > censo.out &" %}
    </div>
<div id="tab-2-2" class="tabcontent tab-id-2" style="text-align:justify">
{% capture struc_file %}
$CENSO global configuration file: .censorc
$VERSION:1.2.0 

ORCA: /home/software/cluster/orca_5_0_4_linux_x86-64_openmpi411
ORCA version: 5.0.4
GFN-xTB: /home/abt-grimme/AK-bin/xtb
CREST: /home/abt-grimme/AK-bin/crest
mpshift: /path/including/binary/mpshift-binary
escf: /path/including/binary/escf-binary

#COSMO-RS
ctd = BP_TZVP_C30_1601.ctd cdir = "/software/cluster/COSMOthermX16/COSMOtherm/CTDATA-FILES" ldir = "/software/cluster/COSMOthermX16/COSMOtherm/CTDATA-FILES"
$ENDPROGRAMS

$CRE SORTING SETTINGS:
$GENERAL SETTINGS:
nconf: all                       # ['all', 'number e.g. 10 up to all conformers'] 
charge: 0                        # ['number e.g. 0'] 
unpaired: 0                      # ['number e.g. 0'] 
solvent: water                   # ['gas', 'acetone', 'acetonitrile', 'aniline', 'benzaldehyde', 'benzene', 'ccl4', '...'] 
prog_rrho: xtb                   # ['xtb'] 
temperature: 298.15              # ['temperature in K e.g. 298.15'] 
trange: [273.15, 378.15, 5]      # ['temperature range [start, end, step]'] 
multitemp: on                    # ['on', 'off'] 
evaluate_rrho: on                # ['on', 'off'] 
consider_sym: on                 # ['on', 'off'] 
bhess: on                        # ['on', 'off'] 
imagthr: automatic               # ['automatic or e.g., -100    # in cm-1'] 
sthr: automatic                  # ['automatic or e.g., 50     # in cm-1'] 
scale: automatic                 # ['automatic or e.g., 1.0 '] 
rmsdbias: off                    # ['on', 'off'] 
sm_rrho: alpb                    # ['alpb', 'gbsa'] 
progress: off                    # ['on', 'off'] 
check: on                        # ['on', 'off'] 
prog: orca                       # ['tm', 'orca'] 
func: r2scan-3c                  # ['b3-lyp', 'b3lyp', 'b3lyp-3c', 'b3lyp-d3', 'b3lyp-d3(0)', 'b3lyp-d4', 'b3lyp-nl', '...'] 
basis: automatic                 # ['automatic', 'def2-TZVP', 'def2-mSVP', 'def2-mSVP', 'def2-mSVP', 'def2-mSVP', '...'] 
maxthreads: 1                    # ['number of threads e.g. 2'] 
omp: 1                           # ['number cores per thread e.g. 4'] 
balance: off                     # ['on', 'off'] 
cosmorsparam: automatic          # ['automatic', '12-fine', '12-normal', '13-fine', '13-normal', '14-fine', '...'] 

$PART0 - CHEAP-PRESCREENING - SETTINGS:
part0: on                        # ['on', 'off'] 
func0: b97-d3                    # ['b3-lyp', 'b3lyp', 'b3lyp-3c', 'b3lyp-d3', 'b3lyp-d3(0)', 'b3lyp-d4', '...'] 
basis0: def2-SV(P)               # ['automatic', 'def2-SV(P)', 'def2-TZVP', 'def2-mSVP', 'def2-mSVP', 'def2-mSVP', '...'] 
part0_gfnv: gfn2                 # ['gfn1', 'gfn2', 'gfnff'] 
part0_threshold: 4.0             # ['number e.g. 4.0'] 

$PART1 - PRESCREENING - SETTINGS:
# func and basis is set under GENERAL SETTINGS
part1: on                        # ['on', 'off'] 
smgsolv1: smd                    # ['alpb_gsolv', 'cosmo', 'cosmors', 'cosmors-fine', 'cpcm', 'dcosmors', '...'] 
part1_gfnv: gfn2                 # ['gfn1', 'gfn2', 'gfnff'] 
part1_threshold: 3.5             # ['number e.g. 5.0'] 

$PART2 - OPTIMIZATION - SETTINGS:
# func and basis is set under GENERAL SETTINGS
part2: on                        # ['on', 'off'] 
prog2opt: prog                   # ['tm', 'orca', 'prog', 'automatic'] 
part2_threshold: 2.5             # ['number e.g. 4.0'] 
sm2: smd                         # ['cosmo', 'cpcm', 'dcosmors', 'default', 'smd'] 
smgsolv2: smd                    # ['alpb_gsolv', 'cosmo', 'cosmors', 'cosmors-fine', 'cpcm', 'dcosmors', '...'] 
part2_gfnv: gfn2                 # ['gfn1', 'gfn2', 'gfnff'] 
ancopt: on                       # ['on'] 
hlow: 0.01                       # ['lowest force constant in ANC generation, e.g. 0.01'] 
opt_spearman: on                 # ['on', 'off'] 
part2_P_threshold: 99            # ['Boltzmann sum threshold in %. e.g. 95 (between 1 and 100)'] 
optlevel2: automatic             # ['crude', 'sloppy', 'loose', 'lax', 'normal', 'tight', 'vtight', 'extreme', '...'] 
optcycles: 8                     # ['number e.g. 5 or 10'] 
spearmanthr: -4.0                # ['value between -1 and 1, if outside set automatically'] 
radsize: 10                      # ['number e.g. 8 or 10'] 
crestcheck: off                  # ['on', 'off'] 

$PART3 - REFINEMENT - SETTINGS:
part3: on                        # ['on', 'off'] 
prog3: prog                      # ['tm', 'orca', 'prog'] 
func3: pw6b95                    # ['b3-lyp', 'b3lyp', 'b3lyp-3c', 'b3lyp-d3', 'b3lyp-d3(0)', 'b3lyp-d4', 'b3lyp-nl', '...'] 
basis3: def2-TZVPD               # ['DZ', 'QZV', 'QZVP', 'QZVPP', 'SV(P)', 'SVP', 'TZVP', 'TZVPP', 'aug-cc-pV5Z', '...'] 
smgsolv3: smd                    # ['alpb_gsolv', 'cosmo', 'cosmors', 'cosmors-fine', 'cpcm', 'dcosmors', '...'] 
part3_gfnv: gfn2                 # ['gfn1', 'gfn2', 'gfnff'] 
part3_threshold: 99              # ['Boltzmann sum threshold in %. e.g. 95 (between 1 and 100)'] 

$NMR PROPERTY SETTINGS:
$PART4 SETTINGS:
part4: off                       # ['on', 'off'] 
couplings: on                    # ['on', 'off'] 
progJ: prog                      # ['tm', 'orca', 'prog'] 
funcJ: pbe0                      # ['b3-lyp', 'b3lyp', 'b3lyp-3c', 'b3lyp-d3', 'b3lyp-d3(0)', 'b3lyp-d4', 'b3lyp-nl', '...'] 
basisJ: def2-TZVP                # ['DZ', 'QZV', 'QZVP', 'QZVPP', 'SV(P)', 'SVP', 'TZVP', 'TZVPP', 'aug-cc-pV5Z', '...'] 
sm4J: smd                        # ['cosmo', 'cpcm', 'dcosmors', 'smd'] 
shieldings: on                   # ['on', 'off'] 
progS: prog                      # ['tm', 'orca', 'prog'] 
funcS: pbe0                      # ['b3-lyp', 'b3lyp', 'b3lyp-3c', 'b3lyp-d3', 'b3lyp-d3(0)', 'b3lyp-d4', 'b3lyp-nl', '...'] 
basisS: def2-TZVP                # ['DZ', 'QZV', 'QZVP', 'QZVPP', 'SV(P)', 'SVP', 'TZVP', 'TZVPP', 'aug-cc-pV5Z', '...'] 
sm4S: smd                        # ['cosmo', 'cpcm', 'dcosmors', 'smd'] 
reference_1H: TMS                # ['TMS'] 
reference_13C: TMS               # ['TMS'] 
reference_19F: CFCl3             # ['CFCl3'] 
reference_29Si: TMS              # ['TMS'] 
reference_31P: TMP               # ['TMP', 'PH3'] 
1H_active: on                    # ['on', 'off'] 
13C_active: on                   # ['on', 'off'] 
19F_active: off                  # ['on', 'off'] 
29Si_active: off                 # ['on', 'off'] 
31P_active: off                  # ['on', 'off'] 
resonance_frequency: 300.0       # ['MHz number of your experimental spectrometer setup'] 

$OPTICAL ROTATION PROPERTY SETTINGS:
$PART5 SETTINGS:
optical_rotation: off            # ['on', 'off'] 
funcOR: pbe                      # ['functional for opt_rot e.g. pbe'] 
funcOR_SCF: r2scan-3c            # ['functional for SCF in opt_rot e.g. r2scan-3c'] 
basisOR: def2-SVPD               # ['basis set for opt_rot e.g. def2-SVPD'] 
frequency_optical_rot: [589.0]   # ['list of freq in nm to evaluate opt rot at e.g. [589, 700]'] 
$END CENSORC
{% endcapture %}
{% include codecell.html content=struc_file style="font-size:10px" %}
</div>

The best structure found is written to `coord.enso_best`, the whole ensemble after part 2 to `enso_ensemble_part2.xyz` and the refined ensemble after part 3 to `enso_ensemble_part3.xyz`. Compare the ranking of the conformers with the GFN2-xTB ensemble resulting with **crest**.

## Optional
With **censo**, also NMR computations can be done. Use the refined ensemble as input for an additional **censo** calculation where every part is turned of except part 4.

{% include note.html content='The NMR calculation can also be done together with the refinment in one calculation by activating all the respective parts with the `censorc`.'%}

