---
layout: post
title:  "Mixed Traffic"
date:   2020-11-23
---

<p class="intro"><span class="dropcap">M</span>ixed traffic in MATSim brings more opportunities. Can we use different modalities on the same network? What would that enable us to do?</p>

<!-- just type out the text without html -->
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Different modalities on the same network create opportunities to build scenarios that represent the real world in much better manner than a single-modal network.
Furthermore, having modalities such as ride-sharing vehicles and regular vehicles on the same network can enable us to test the algorithm that ride-sharing vehicles (taxis - dynamic agents) are using for decision making.
 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Having different modalities on the same network is something that has already been implemented before. However, modalities that I am referring to are regular cars, bicycles, public transportation, etc. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The question is how to create a network that contains regular vehicles mixed with ride-sharing vehicles (taxis). In my current research, I am trying to implement Peagu's example where the network will contain a mixed traffic of regular vehicles with ride-sharing vehicles. The code for this example can be found <a href="https://github.com/NikolaAndro/MATSim" >here</a>.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The first solution for having multiple modalities in one simulation is that we can have multi layered network. For each mode there can be a layer, and those layers are connected to each other over the nodes. However, after the research project NetCap in ETH, Switzerland, we are able to have a fully multi modal network without having to have layers. This package refers to having PT (public transit) and private transit in the same network so regular vehicles (cars) and busses can compete for slots on the network and interact with each other. Before this package, we had multiple layers so cars would not be impacted by bus stopping or impacted by slow bus driving.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; This package, however, does not refer to the problem of having ride-sharing vehicles and regular vehicles on the same network while impacting each other. Since ride-sharing vehicles are car based mode, the simulation is treating them as cars.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; According to my new findings, since taxis are car based modality, there is no need for another network, or a multilayered network. Hence, we just need to add regular cars and vehicles correctly in configuration file and simulation should run correctly.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; You can checkout <a href="https://github.com/NikolaAndro/MATSim" >Pigou's Example</a>.


In the following image, you can see a scenario with regular cars and taxis on the same sigle-layered netwrok.

<p align="center">
  <img src="../assets/img/cars_and_taxis.PNG?raw=true">
</p>

