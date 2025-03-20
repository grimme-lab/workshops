---
layout: default
title: Additional Features
parent: "CREST"
nav_order: 7
has_children: false
permalink: page/crest/addition
---

# Additional Feature

## Ensemble Sorting Tool

**crest** provides a feature to sort a given ensemble or trajectory according to energies and to remove duplicates.
The energies are listed in the comment line of each structure (the second line, right after the number of atoms per structure). 

This is especially helpful for combined ensembles resulting from different **crest** runs. It can be invoked with the `--cregen` keyword.

```bash
crest struc.xyz --cregen <ensemble file>
```

where `struc.xyz` is a random conformer of the structure and `<ensemble file>` is the ensemble. The sorted ensemble is written to the file `<ensemble file>.sorted`. 

The standard **crest** sorting flags can be used as well, such as `--ewin <REAL>`. A complete list of keywords can be found in the [documentation](https://crest-lab.github.io/crest-docs/page/documentation/keywords.html#ensemble-sorting-options).

## Clustering

**crest** also supports clustering of ensembles, leaving only the most representative conformers. The sorting is done using an automatic principal component analysis (PCA) and k-Means clustering algorithm.
It is invoked with the `--cluster` flag and can be combined with the `--cregen` sorting, or used for ensemble searches, where clustering is performed after the default search. The resulting reduced ensemble can be found in `crest_clustered.xyz` along with the usual output files.
An optional argument after the flag can be provided to, for example, only keep a certain number of structures (`--cluster <INT>`). Further options can be found in the [documentation](https://crest-lab.github.io/crest-docs/page/documentation/keywords.html#pca-clustering-options).

## Ensemble File Splitting

**crest** allows you to split an ensemble into individual conformers in different directories using the `--splitfile` flag:

```bash
crest --splitfile <ensemble file>
```
This will create a directory called `SPLIT`, which contains directories named `STRUCX`, where X is the number of the respective conformer. Each of these directories contains a structure file of the conformer.

## Properties for Ensembles

You can also compute various properties of an ensemble using **crest**. This feature is invoked with the `--forall` flag:

```bash
crest --forall <ensemble file>
```

This can be combined with the `--prop` flag. For example, `--prop singlepoint` will compute the single-point energy of each conformer and list the respective energies as well as the ensemble average. 
`--prop hess` invokes additional Hessian and thermocorrection computations, and `--prop autoIR` generates a vibrational spectrum of the ensemble, written to `crest.vibspectrum`.

## Trajectory Optimization

With **crest**, you can also optimize the structures of an ensemble or trajectory file, such as the ones resulting from **xtb** MD simulations.
This can be done with different GFN methods and is invoked with:

```bash
crest --mdopt <FILE>
```

where `<FILE>` is the trajectory/ensemble file. The optimized and sorted structures will be written to the `crest_ensemble.xyz` file.
