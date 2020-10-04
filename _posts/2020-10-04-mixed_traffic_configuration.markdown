---
layout: post
title:  "Mixed Traffic Configuration"
date:   2020-10-04
---

<p class="intro"><span class="dropcap">C</span>onfiguring mixed traffic in MATSim is not a very popular topic. Hence, here I will be posting updates on mixed traffic configuration.</p>

As we can already see from other examples from MATSim researchers, in order to have a ride-sharing vehicles network, we have to enter that module in our config file. For instance, in 
<a href="https://github.com/NikolaAndro/MATSim/blob/master/Pigou's%20Example/scenarios/Pigou_multiModal_2020/mielec_taxi_config_rulebased.xml">Pegou's example</a> that I am 
implementing, that configuration looks something like this:

{% highlight ruby %}
<module name="multiModeTaxi">
	<parameterset type="taxi">
		<param name="destinationKnown" value="false"/>
		<param name="vehicleDiversion" value="false"/>
		<param name="pickupDuration" value="120"/>
		<param name="dropoffDuration" value="60"/>
		<param name="onlineVehicleTracker" value="false"/>

		<param name="taxisFile" value="taxis-25.xml"/>

		<param name="timeProfiles" value="true"/>
		<param name="detailedStats" value="true"/>

		<!-- This is a rule based dispatch algorithm -->
		<parameterset type="RuleBasedTaxiOptimizer"/>

	</parameterset>
</module>
{% endhighlight %}

In this example we can see different parameters of the dynamic ageents (ride-sharing vehicles/taxis). One of the parameters is a <a href="https://github.com/NikolaAndro/MATSim/blob/master/Pigou's%20Example/scenarios/Pigou_multiModal_2020/taxis-25.xml">taxisFile</a> 
which contains all the taxis that are supposed to be on the network. 

