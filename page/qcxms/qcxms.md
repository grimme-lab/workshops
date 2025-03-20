---
layout: default
nav_order: 6
title: QCxMS
has_children: true
permalink: page/qcxms
toc: false
---
# {{page.title}}
{: .no_toc}

QCxMS is a quantum chemical (QC) based program that enables users to calculate mass spectra (MS) using Born-Oppenheimer Molecular Dynamics (MD). 

For detailed instructions on how to run QCxMS, please see the [documentation](https://xtb-docs.readthedocs.io/en/latest/qcxms_doc/qcxms_run.html).

QCxMS2, the successor of QCxMS, relies on automated reaction network discovery, which is done usually on higher-level DFT/WFT PESs.

It can directly be invoked for a structure as:

```bash
qcxms2 struc.xyz -T <INT>
```

where `-T <INT>` is used to define the number of cores used for the calculation. Per default, a EI calculation is performed.
Further options can be found in the [documentation](https://xtb-docs.readthedocs.io/en/latest/qcxms2_doc/qcxms2_run.html#qcxms2-run).

{% include warning.html content="It is recommended to use the energetically most stable conformer as input generated, *e.g.*, with **crest**."%}


{% include note.html content='The default values of QCxMS and QCxMS2 are not always giving the best results, but are set to cover the majority of systems. Molecules have different characteristics that can significantely influence the outcome. Changing the input settings can improve upon the final result, e.g. decreasing the molecular ion peak abundance or producing more low m/z fragments.'%}


## Literature
- **QCxMS ||** Koopman, Jeroen, and Grimme, Stefan. "From QCEIMS to QCxMS: A Tool to Routinely Calculate CID Mass Spectra Using Molecular Dynamics." 
[*Journal of the American Society for Mass Spectrometry*, **2021**, *32*, 1735-1751.](https://pubs.acs.org/doi/10.1021/jasms.1c00098)
{: .fs-6 .fw-300 }

- **QCxMS2 ||** Gorges, Johannes, and Grimme, Stefan. "QCxMS2 – a program for the calculation of electron ionization mass spectra via automated reaction network discovery" 
[*Physical Chemistry Chemical Physics*, **2025**.](https://pubs.rsc.org/pl/content/articlelanding/2025/cp/d5cp00316d)
{: .fs-6 .fw-300 }

