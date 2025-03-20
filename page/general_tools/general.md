---
layout: default
nav_order: 2
title: General Tools
has_children: false
permalink: page/general_tools
toc: false
---
# {{page.title}}
{: .no_toc}

## PubGrep

PubGrep is a command line tool that can automatically get random conformer structure data from the PubChem database, if it is available. This tool is very useful to quickly get a 3D structure of a compound. It comes either as a bash script or a Python implementation, both found on [GitHub](https://github.com/grimme-lab/PubGrep). The bashscipt can directly be used after making it executable, *e.g.*,:

```bash
chmod u+x PubGrep
```

The Python implementation can be installed with pip into the current environment:

```bash
pip install -e .
```

A complete list of functions is shown by executing

```bash
PubGrep --help
```

You can get a 3D structure by using, for example, the compound name or the PubGrep ID:

```bash
PubGrep <Name>
PubGrep <ID> --input cid
``` 

The result is per default an *.sdf* file named after the CID. If there is no 3D structure on PubChem, a 2D to 3D converter is used to generate a random conformer which must not be the energetically favored one.
{% include warning.html content='The 2D to 3D structure conversition requires a working installation of **xtb** that is accessible by the script, *e.g.*, by adding **xtb** to your `path` variable (see the [xtb chapter](/page/xtb/installation)).
'%}

## Structure converter

The MCTC library provides access to many commonly required routines for structure handling and also has a stand-alone for structure converstion, namely the `mctc-convert`.
The library is available on [github](https://github.com/grimme-lab/mctc-lib) and can be compiled with meson, cmake, or fpm with standard fortran compiler.
A precompiled `mctc-convert` binary is also available on [github](https://github.com/grimme-lab/mctc-lib/releases/tag/v0.3.1). After extracting the `mctc-convert-0.3.1.tar.xz` archive, you can find the binary in the extracted *bin* directory. You can copy it to a path of your liking.
Alternatively, you can install the mctc-lib via Homebrew:

```bash
brew tap grimme-lab/qc
brew install crest
```

The mctc-convert only requires an input coordinate file and writes the respective output file:

```bash
mctc-convert <input file> <output file>
```

Determining the file format of the input and output file is done automatically according to the respective file extension. For example, *.xyz* is recognized as Xmol file, while *.coord* defines the Turbomole format.
Supported formats are:

|------------------------------------------|----------------------------------|
| Format                                   | File extension                   |
|------------------------------------------|----------------------------------|
| Xmol/xyz files                          | xyz, log                        |
| Turbomole’s coord, riper’s periodic coord | tmol, coord                     |
| DFTB+ genFormat geometry inputs          | gen                              |
| VASP’s POSCAR/CONTCAR input files        | vasp, poscar, contcar           |
| Protein Database files (single files)    | pdb                              |
| Connection table files (molfile, SDF)    | mol, sdf                         |
| Gaussian’s external program input        | ein                              |
| JSON input with qcschema structure       | json                             |
| Chemical JSON input                      | cjson                            |
| FHI-AIMS' input files                    | geometry.in                      |
| Q-Chem molecule block inputs             | qchem                            |
|------------------------------------------|----------------------------------|

Further information are shown by using the *--help* command (`mctc-convert --help`).


## RMSD tool

The MCTC RMSD tool can be used for calculating the root mean square deviation (RMSD) of two structures. This is useful qunatifying structural differences, *e.g.*, to identify similar structures. It is available on [github](https://github.com/grimme-lab/rmsd-tool) including [precompiled binaries](https://github.com/grimme-lab/rmsd-tool/releases). After extracting the `mctc-rmsd-0.1.1.tar.xz` archive, the `mctc-binary` can be found in the extracted *bin* directory and can be copied to a place of your liking.
It is called with

```bash
mctc-rmsd struc1.xyz struc2.xyz
```

Additional filters can be applied to, *e.g.*, excluding hydrogen atoms by using the flag *--filter heavy*. Further information can be found with the *--help* flag (`mctc-rmsd --help`).
