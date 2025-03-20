---
layout: default
title: Installation
parent: "xtb"
nav_order: 1
has_children: false
permalink: /page/xtb/installation
---

# Installation

## General Considerations

The **xtb** software is open-source and available under the LGPL 3.0 license on GitHub. This guide provides a brief summary of the official [installation guide](https://xtb-docs.readthedocs.io/en/latest/setup.html).

If you encounter any issues, refer to the full documentation or open an [issue on GitHub](https://github.com/grimme-lab/xtb/issues) for support.

{% include warning.html content="The primary operating system (OS) for developing and using **xtb** is Linux. While installation on Windows and macOS is possible, support for these platforms may be more limited." %}

## Easy Installation

The simplest way to install **xtb** is by downloading the [precompiled binaries](https://github.com/grimme-lab/xtb/releases). There, you have also access a bleeding-edge version of the program.

After downloading the appropriate version, extract the files, make them executable, and add the program to your `PATH` variable for easy access:

```bash
tar -xvf xtb*.tar.xz
chmod +x ./xtb-dist/bin/xtb
export PATH=$PWD/xtb-dist/bin:$PATH
```

Alternatively, you can copy the **xtb** binary to a directory of your choice, *e.g.,* your `bin` folder.  
To verify that the executable is correctly linked, use:  

```bash
which xtb
```
And check the installed version with:
```bash
xtb --version
```

{% include tip.html content='You can add the full path to your **xtb** executable to the Bash shell configuration file (~/.bashrc) to automatically load **xtb** in new sessions.'%}


## Homebrew Support

**xtb** can also be installed with Homebrew.
The support is provided by an additional [GitHub](https://github.com/grimme-lab/homebrew-qc) repository that provides access also to additional software.
**xtb** can be installed on MacOS via

```bash
brew tap grimme-lab/qc
brew install xtb
```

## Important settings
To work properly also for large systems, it is recommended to unlimit the system stack size, *e.g.*, with bash by:

```bash
ulimit -s unlimited
```

This can also be included in the `~/.bashrc` file.

Further, to allow parallelisation, a reasonable large number of OMP stacksize must be provided, `e.g.`:

```bash
export OMP_STACKSIZE=4G
```

and the number of cores to be used by **xtb** are set with

```bash
export OMP_NUM_THREADS=<ncores>,1
```

## Compilation  
A more advanced approach is to compile **xtb** from source. Native compilation offers several advantages over precompiled binaries, such as generating a system-optimized binary and enabling in-place modifications to the software.  

This guide follows a minimalistic build process using the default toolchain: the `meson` build system and the `ifort`/`icc` compilers.  

First step is to clone the official GitHub repository via:
```bash
git clone https://github.com/grimme-lab/xtb.git
```

Then, define the Fortran and C compilers, which can be installed via Intel's [Developer Toolkit](https://www.intel.com/content/www/us/en/developer/tools/oneapi/toolkits.html#base-kit):
```bash
export FC=ifort CC=icc
```

Finally, you can build the project with [Meson](https://mesonbuild.com/):
```bash
meson setup build --buildtype=release
meson compile -C build
```

Alternatively, `gfortran`/`gcc` compilers are also supported. For a complete list of supported compilers and backends, please see the [github page](https://github.com/grimme-lab/xtb?tab=readme-ov-file#semiempirical-extended-tight-binding-program-package).
