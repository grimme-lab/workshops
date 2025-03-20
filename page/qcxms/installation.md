---
layout: default
title: Installation
parent: "QCxMS"
nav_order: 2
has_children: false
permalink: page/qcxms/installation
---

# {{ page.title }}

# QCxMS 1

A pre-compiled executable of the latest program version can be found on [GitHub](https://github.com/grimme-lab/QCxMS/releases/tag/latest). Follow the instructions to use QCxMS1 without the need of building anything.

After extracting the file, you will find several files:

| Executable / Folder    | Description |
|------------------------|-------------|
| **qcxms**             | Main program (executable) |
| **pqcxms**            | Script that runs trajectories in parallel locally (executable) |
| **q-batch**           | Script that runs trajectories on a cluster with a queueing system (executable) |
| **getres**            | Script that gives the status of the parallel QCxMS production run (executable) |
| **.XTBPARAM**         | Folder containing xTB parameter files (.param_gfn.xtb, .param_gfn2.xtb, .param_ipea.xtb) |
| **EXAMPLE**           | Folder hosting an example input and coordinate file |

The .XTBPARAM folder has to be placed in your $HOME directory (these files can appear to be hidden).
Further software installation is not required.
For different installation possibilities, please have a look at the [documentation](https://xtb-docs.readthedocs.io/en/latest/qcxms_doc/qcxms_setup.html#).

For easy visualization of the calculated spectra, the **PlotMS** program was developed. An instruction can be found in the [documentation](https://xtb-docs.readthedocs.io/en/latest/qcxms_doc/qcxms_plot.html).
The program is available at the [PlotMS repository](https://github.com/qcxms/PlotMS).
To display the results, we recommend the useage of xmgrace. Exemplary input and coordinate files can be found in the EXAMPLES folder.

## QCxMS 2

A pre-compiled executable of the latest program version can be found on [GitHub](https://github.com/grimme-lab/QCxMS2/releases/tag/latest). Follow the instructions to use QCxMS2 without the need of building anything.

After extracting the file, you will find the excectuable called `qcxms2`.

QCxMS2 requires additionally the following programs that must be available in `$HOME/bin` and named exactly as follows:

| Executable              | Required Version         | Software Repository Link |
|-------------------------|-------------------------|--------------------------|
| **xtb**                | > 6.7.1 (bleeding edge)  | [xtb](https://github.com/grimme-lab/xtb) |
| **crest**              | >= 3.0.2                 | [crest](https://github.com/grimme-lab/crest) |
| **orca**               | >= 6.0.0                 | [orca](https://orcaforum.kofo.mpg.de/) |
| **molbar**             | >= 1.1.3                 | [molbar](https://github.com/qcscine/molbar) |
| **geodesic_interpolate** (optional) | >= 1.0.0 | [geodesic](https://github.com/geodesic-interpolate) |

Further information are available in the [documentation](https://xtb-docs.readthedocs.io/en/latest/qcxms2_doc/qcxms2_setup.html).
