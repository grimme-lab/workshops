---
layout: default
title: Protonation
parent: "CREST"
nav_order: 6
has_children: false
permalink: page/crest/crest
---

# {{ page.title }}

**crest** is also a useful tool for protonating and deprotonating structures. Both can also be combined to tautomerize structures.
In the following, we will try this for the dipeptide consisting of alanine and glycine (Ala-Gly).

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
20

C     2.081440     0.615100    -0.508430
C     2.742230     1.824030    -1.200820
N     4.117790     1.799870    -1.190410
C     4.943570     2.827040    -1.822060
C     6.440080     2.569360    -1.637600
O     7.351600     3.252270    -2.069090
N     0.610100     0.695090    -0.538780
O     2.095560     2.724940    -1.739670
O     6.705220     1.463410    -0.897460
H     0.303080     1.426060     0.103770
H     0.338420     1.050680    -1.460480
C     2.488753    -0.593400    -1.198448
H     2.416500     0.557400     0.532050
H     4.614100     1.081980    -0.670550
H     4.699850     3.794460    -1.373720
H     4.722890     2.844690    -2.894180
H     7.687400     1.448620    -0.860340
H     2.029201    -1.457008    -0.719999
H     2.170233    -0.542411    -2.238576
H     3.572730    -0.688405    -1.154998
{% endcapture %}
{% include codecell.html content=struc_file_1 style="font-size:10px" %}
</div>

## Protonation

Protonation screening can be requested with:

```bash
crest struc.xyz --protonate
```

This uses GFN2-xTB by default. All protomers found by **crest** are stored in `protonated.xyz`.

Compute the protomers for Ala-Gly and determine the energetic ordering. Does the lowest protomer align with chemical intuition?

## Deprotonation

Similar to protonation, the deprotonation screening for Ala-Gly can be invoked with:

```bash
crest struc.xyz --deprotonate
```
All found structures are stored in `deprotonated.xyz`.

Compute the protomers for Ala-Gly and determine the energetic ordering.


## Combining Protonation and Deprotonation

**crest** can combine the protonation and deprotonation screenings to find tautomers.

```bash
crest struc.xyz --tautomerize
```

The found tautomers will be stored at `tautomers.xyz`.
Compute and check all the tautomers. 
Can you find the zwitterion? If not, why?


<div class="tab card">
  <button class="tablinks tab-id-5-4 active" onclick="openTabId(event, 'question-5-1', 'tab-id-5-4')" id="open-5-4">{{ site.data.icons.question }} <strong>Question</strong></button>
  <button class="tablinks tab-id-5-4" onclick="openTabId(event, 'hint-5-1', 'tab-id-5-4')">{{ site.data.icons.hint }} <strong>Hint</strong></button>
  <button class="tablinks tab-id-5-4" onclick="openTabId(event, 'solution-5-1', 'tab-id-5-4')">{{ site.data.icons.solution }} <strong>Solution</strong></button>
</div>

<!-- Tab content -->
<div id="question-5-1" class="tabcontent tab-id-5-4" style="text-align:justify">
  <p><strong>Q:</strong> How can you find the zwitter ion?</p>
</div>

<div id="hint-5-1" class="tabcontent tab-id-5-4" style="text-align:justify">
  <p><strong>Hint:</strong> In which environment do you usually find this type of compound?</p>
</div>

<div id="solution-5-1" class="tabcontent tab-id-5-4" style="text-align:justify">
  <p><strong>Solution:</strong> Add implicit solvation to stabilize charged species via <code>--alpb water</code></p>
</div>
{% include defaulttab.html id="open-5-4" %}
