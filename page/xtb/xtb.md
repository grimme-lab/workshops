---
layout: default
nav_order: 3
title: xtb
has_children: true
permalink: page/xtb
toc: false
---
# {{page.title}}
{: .no_toc}


The **xtb** program provides access to the GFN1-xTB, GFN2-xTB, and GFN-FF methods, along with various functionalities, many of which will be covered in this workshop.  
A complete documentation is available [online](https://xtb-docs.readthedocs.io/en/latest/index.html).  

Beyond its functionalities, the xTB methods are known for their broad applicability to systems containing elements up to radon (Z=86), robust and efficient performance, and ease of use in practical applications.  

For this workshop, please use xtb version 6.7.0 or later.  

{% include image.html file="toc.png" alt="CREST" max-width=750 %}


## Literature

For deeper insights into the mathematical construction and technical details of the here used GFNn-xTB methods please read the original literature (excerpt):


- **GFN1-xTB ||** Stefan Grimme, Christoph Bannwarth, and Philip Shushkov. “A robust and accurate tight-binding quantum chemical method for structures, vibrational frequencies, and noncovalent interactions of large molecular systems parametrized for all spd-block elements (Z= 1–86)”.
[*J. Chem. Theory Comput.*, **2017**, *13 (5)*, 1989-2009.](https://doi.org/10.1021/acs.jctc.7b00118)
{: .fs-6 .fw-300 }

- **GFN2-xTB ||** Christoph Bannwarth, Sebastian Ehlert, and Stefan Grimme. “GFN2-xTB—An accurate and broadly parametrized self-consistent tight-binding quantum chemical method with multipole electrostatics and density-dependent dispersion contributions”. 
[*J. Chem. Theory Comput.*, **2019**, *15(3)*, 1652–1671.](https://doi.org/10.1021/acs.jctc.8b01176)
{: .fs-6 .fw-300 }

- **GFN-FF ||** Sebastian Spicher and Stefan Grimme. “Robust atomistic modeling of materials, organometallic, and biochemical systems”. 
[*Angew. Chem. Int. Ed.*, **2020**,  *59(36)*, 15665–15673.](https://doi.org/10.1002/anie.202004239)
{: .fs-6 .fw-300 }

- **Review 1 ||** Christoph Bannwarth, Eike Caldeweyher, Sebastian Ehlert, Andreas Hansen, Philipp Pracht, Jakob Seibert, Sebastian Spicher, and Stefan Grimme. “Extended tight-binding quantum chemistry methods”.
[*Wiley Interdisciplinary Reviews: Computational Molecular Science 11*, **2021**, *2*,  e1493.](https://doi.org/10.1002/wcms.1493)
{: .fs-6 .fw-300 }

- **Review 2 ||** Albert Katbashev, Marcel Stahn, Thomas Rose, Vahide Alizadeh, Marvin Friede, Christoph Plett, Pit Steinbach, and Sebastian Ehlert, ”Overview on Building Blocks andApplications of Efficient and Robust Extended Tight Binding”.
[*The Jpurnal of Physical Chemistry A*, **2025**, *129*.](https://pubs.acs.org/doi/10.1021/acs.jpca.4c08263)
{: .fs-6 .fw-300 }

- **mcGFN-FF ||** Stefan Grimme and Thomas Rose. “mcGFN-FF: an accurate force field for optimization and energetic screening of molecular crystals”. 
[*Zeitschrift fuer Naturforschung*, **2024**, *79(4)*, 191-200.](https://doi.org/10.1515/znb-2023-0088)
{: .fs-6 .fw-300 }

- **aISS ||** Christoph Plett and Stefan Grimme. “Automated and efficient generation of general molecular aggregate structures”. 
[*Angew. Chem. Int. Ed.*, **2023**, *62(4)*, e202214477.](https://doi.org/10.1002/anie.202214477)
{: .fs-6 .fw-300 }

- **ONIOM ||** Christoph Plett, Albert Katbashev, Sebastian Ehlert, Markus Bursch, and Stefan Grimme. “ONIOM meets xtb: efficient, accurate, and robust multi-layer simulations across the periodic table”. 
[*Phys. Chem. Chem. Phys.*, **2024**, *26*, 12610.](https://doi.org/10.1039/D3CP02178E)
{: .fs-6 .fw-300 }
