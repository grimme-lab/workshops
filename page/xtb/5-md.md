---
layout: default
title: MD
full_title: Molecular-dynamics
parent: "xtb"
nav_order: 7
has_children: false
permalink: page/xtb/MD
---

# Molecular Dynamics Simulations

**xtb** is also capable of performing molecular dynamics (MD) simulations.  
An MD simulation with pre-optimization can be initiated with:  

```bash
xtb struc.xyz --omd
```

{% include note.html content='An MD simulation can also be started with the `--md` flag, but the input structure should be reasonable. Otherwise, the MD simulation may become unstable.' %}  

To have more detailed control over the MD simulation, you can provide an **xtb** input file. The following example shows the default settings, which can be adjusted as needed.  


 ```bash
$md
   temp=298.15 # temperature in K
   time= 50.0  # Total time of MD in ps
   dump= 50.0  # Interval of saving a structure in fs
   step=  4.0  # Single time step in fs
   velo=false  # Don't print out velocities
   nvt =true   # Retain NVT ensemble
   hmass=4     # Mass of H atoms
   shake=2     # Apply shake algorithm to all bonds
   sccacc=2.0  # Accuracy of SCC iterations
$end
```

Further keywords and explanations can be found in the [documentation](https://xtb-docs.readthedocs.io/en/latest/md.html#parameters).  
{% include note.html content='If the MD simulation becomes unstable, you can try lowering the time step or increasing the hydrogen mass. This is particularly recommended when using GFN-FF.' %}  

## Exercise 1

Try running an MD simulation using GFN-FF with the ALPB(water) solvation model and default settings.  

<!-- Tab links -->
<div class="tab card">
  <button
    class="tablinks tab-id-1"
    onclick="openTabId(event, 'struc-1', 'tab-id-1')"
    id="open-1">
    {{ site.data.icons.codefile }} <code>bacillaene.xyz</code>
  </button>
</div>
<!-- Tab content -->
<div id="struc-1" class="tabcontent tab-id-1" style="text-align:justify">
{% capture struc_file_1 %}
  90
 
 C         -5.3127996594       -2.4157946011       -0.5090291244
 C         -6.6369198591       -2.2744765141       -0.3505867691
 C         -4.5376337067       -1.9989947690       -1.6511538708
 C         -7.4911082799       -1.4906802100       -1.3353795445
 C         -7.3417027536       -2.8130153570        0.8534300295
 C         -6.9820968905       -0.0260037238       -1.4231824713
 C         -3.2303223550       -1.6498120479       -1.6254976982
 C         -2.4648530707       -1.4782784301       -0.4345685359
 C         -1.1490119425       -1.1466912716       -0.3267799699
 C         -0.2345729980       -0.9625082034       -1.4997955626
 C         -0.6049768456       -0.9722141905        0.9890332154
 C          0.6701604636       -0.6330961686        1.2870390935
 C          1.1341096011       -0.4761647542        2.6269132552
 C          2.3830259753       -0.1235992724        3.0110310022
 C          3.4734843635        0.1679005598        2.1268262297
 C          4.6931387856        0.5393278145        2.5267510375
 C          5.8304304131        0.8677548326        1.6003866159
 N          5.4283570547        0.8855111783        0.2104033711
 C          5.3166273681       -0.1533114661       -0.6067536733
 C          6.0134079054       -1.4661798013       -0.2726105716
 O          4.7074640990       -0.0705419639       -1.6861449989
 C          7.5144666461       -1.3152943375       -0.5941160582
 O          5.4313708211       -2.5035661443       -1.0272412069
 C         -6.7935147347        0.4641208344       -0.0003944175
 O         -7.7403733383        0.5228053447        0.7742620645
 N         -5.5106869286        0.7636403711        0.3110847277
 C         -4.9463300150        1.1535464336        1.5274406520
 C         -3.6739854047        1.6059179412        1.5754484283
 C         -5.7878061510        1.0225637475        2.7522984886
 C         -2.7844664843        1.8243840709        0.4767015254
 C         -1.5364316121        2.3145689941        0.6208013650
 C         -0.6655220004        2.5888732490       -0.4843830298
 C          0.5487325406        3.1343609346       -0.3631391694
 C          8.3298335983       -2.5431938358       -0.1704211284
 C          9.6891088069       -2.5276652589       -0.8678074623
 C          8.5197655075       -2.5906603796        1.3443209467
 O         -8.8586444577       -1.4991160896       -1.0023350180
 C          1.4399210852        3.4740558350       -1.5251049648
 C          2.6756050844        2.6104389356       -1.3716483915
 C          1.8111558123        4.9585806785       -1.5160495647
 O          2.6206023923        1.5056225590       -2.0814961045
 O          3.6041031244        2.8850885925       -0.6340527724
 H         -4.7625204190       -2.9056795986        0.2836333196
 H         -5.0509303359       -2.0042601899       -2.6049219243
 H         -7.4349047919       -1.9513459821       -2.3302603369
 H         -6.6760991929       -3.4329009729        1.4477280383
 H         -8.2048607459       -3.4019112683        0.5445011777
 H         -7.7116749441       -1.9955343308        1.4750390520
 H         -6.0619084015        0.0254594956       -1.9985287387
 H         -7.7560134130        0.5683074568       -1.9132455671
 H         -2.7489218428       -1.4394091975       -2.5706796840
 H         -3.0129717265       -1.5960544885        0.4909743144
 H         -0.7561184183       -1.0725573851       -2.4442035526
 H          0.5638309381       -1.7039098370       -1.4666980415
 H          0.2258577807        0.0242190429       -1.4708519245
 H         -1.2956296326       -1.1246557687        1.8098949728
 H          1.3745898015       -0.4696821456        0.4862918222
 H          0.3981454779       -0.6600516684        3.4004310551
 H          2.5974468939       -0.0405121044        4.0685973172
 H          3.2726215465        0.0815655312        1.0682418239
 H          4.9262739703        0.6324234323        3.5775689496
 H          6.6468639108        0.1562857796        1.7478921113
 H          6.2119507967        1.8653636049        1.8407595221
 H          4.8859889259        1.7105149385       -0.0683642472
 H          5.8575220450       -1.7269366655        0.7774134480
 H          7.6007536957       -1.1797242272       -1.6752148153
 H          7.9082834268       -0.4205120198       -0.1104506371
 H          5.0955504465       -2.0978322698       -1.8442489323
 H         -4.8389468734        0.6790182836       -0.4409166158
 H         -3.2785159256        1.8587339956        2.5484209564
 H         -5.2246095910        1.3178627663        3.6320617997
 H         -6.1254267820       -0.0065165747        2.8692478768
 H         -6.6790660370        1.6429351108        2.6701403518
 H         -3.1292138183        1.6120944762       -0.5273979730
 H         -1.1579767117        2.5402684410        1.6084450304
 H         -1.0491040613        2.3573854617       -1.4703055793
 H          0.9505481083        3.3742128511        0.6120025660
 H          7.7785462919       -3.4349097892       -0.4874864977
 H          9.5694109024       -2.5429149313       -1.9488155636
 H         10.2730806739       -3.3975457026       -0.5768929878
 H         10.2450015890       -1.6328073712       -0.5947376585
 H          9.0991604017       -3.4685164813        1.6200641190
 H          7.5644928769       -2.6459407744        1.8604244387
 H          9.0545665098       -1.7068730142        1.6874964687
 H         -8.9584252351       -0.9401749581       -0.2142721535
 H          0.9490038267        3.1991238510       -2.4619332618
 H          2.4126870178        5.2036544364       -2.3883354398
 H          2.3855713372        5.1906177538       -0.6223783473
 H          0.9080079216        5.5625777336       -1.5263116425
 H          3.4359643823        0.9211814126       -1.9665264904
{% endcapture %}
{% include codecell.html content=struc_file_1 style="font-size:10px" %}
</div>

Next, run another MD simulation with the same settings but adjust the time step to 2.0 fs by providing an input file. For time efficiency, reduce the MD length to 20 ps this time, but please be aware that this is by far not sufficient for production runs.

You can view the resulting trajectory by opening the `xtb.trj` file with tools like **Molden**.  

## MTD simulations
With **xtb**, you can also apply additional potentials during MD simulations to drive the molecule over energy barriers and prevent sampling the same structure repeatedly. These types of simulations are known as Meta-Dynamics (MTD) simulations and can be very useful for exploring the potential energy surface (PES) of a molecule.  
To activate MTD simulations, add the following block to your **xtb** input file:  

```bash
$metadyn
   save=10
   kpush=1.0
   alp=0.2
$end
```

## Exercise 2

Perform a new MD simulation using the **xtb** input file you created earlier, but add a second block to activate the MTD simulation as shown above. Check the resulting trajectory and compare it to the normal MD simulation.  

For more information on the technical aspects of MTD simulations, refer to the [documentation](https://xtb-docs.readthedocs.io/en/latest/mtd.html). For the theoretical background, see the [original publication](https://pubs.acs.org/doi/10.1021/acs.jctc.9b00143).  
