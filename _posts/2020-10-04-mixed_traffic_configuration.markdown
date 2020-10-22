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

In this example we can see different parameters of the dynamic ageents (ride-sharing vehicles/taxis). 

One of the parameters is a <a href="https://github.com/NikolaAndro/MATSim/blob/master/Pigou's%20Example/scenarios/Pigou_multiModal_2020/taxis-25.xml">taxisFile</a> 
which contains all the taxis that are supposed to be on the network. Each ride-sharing vehicle has its starting position. From there, each vehicle should decide which road it will
take in order to reach the desired destination. Vehicle's decision is based on algorithm provided in the config file.

{% highlight ruby %}
	<!-- This is a rule based dispatch algorithm -->
	<parameterset type="RuleBasedTaxiOptimizer"/>
{% endhighlight %}

Regular vehicles (cars) are implemented in a way that we assign the departure and arrival time of a vehicle. We can use this to test how ride-sharing algorithms react on different scenarios. For instance, we could have two different routs to our desired destination. One road is a highway with speed limit of 120 kmph and another road is not a highway and has speed limit of 60 kmph. We could assign many vehicles to go over the highway, which would make the rout with lower speed limit to actually be the faster route. From there, depending on the ride-sharing algorthm's parameters and goals, we can see how ride-sharing vehicles would react. 
