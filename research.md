---
title: Research
nav: research
subnav: exemplar-home
layout: default
---

---

## Approximate Computing
---

### Outline

+ [Motivation](#motivation)

+ [FPGA-based fault emulation](#faultinjection)

+ [Data-path Separation](#dpcp)

+ [Global Fault Optimization](#globalopt)

+ [Publications](#publications)

### <a name="motivation"></a> Motivation 
There are mainly two trends that make the life of IC designers difficult these days:

+ Shrinking CMOS feature sizes (technology scaling)
+ Increasing demand for low-power applications

At a first glance one would say that these are positive trends. But they both have in common that the reliability of future CMOS devices has to suffer. Shrinking feature sizes result in a increasing susceptibility to soft-errors (mainly due to radiation), manufacturing defects and ageing effects. Low-power applications are usually realized by reducing the supply voltage of a circuit as it has a square influence to the dynamic power consumption.
$$P_{dyn} = CV²f$$
The problem is, that the propagation delay of a CMOS inverter is inverse proportional to the supply Voltage. Hence, if we want to reduce the power consumption of a circuit we either have to reduce the operation frequency (nobody wants that!) or we have to operate our circuit very close to timing violations which again results in errors in the circuit.

In general one can say that IC designers have to decide in which direction they want to optimize their circuit:

+ Performance
+ Power
+ Area
+ Reliability




This is what I call the **PPA+R Trade-off**.

__Approximate Computing__ is one approach to tackle this trade-off. The idea is to __relax the need for fully precise or fault-free operations__ in order to __substantially improve the energy efficiency__. Approximate Computing proposes to allow faults in the circuit to save power! Because, if one would tolerate faults within the circuit, one could e.g. further reduce the supply-voltage. One could also further increase the operating frequency, closer to or beyond the limit. One could further scale-down the technology. One could remove redundancy introduced to protect the circuit against soft errors. And so on... Approximate computing looks promising to open up a whole new range of optimizations!

### Potential Fields of Application
Clearly, such an approach is not suitable for all kinds of applications. One will never be able to tolerate faults in an airbag controller, or in the flight controller of an airplane. Applications that seem to be predestined for approximate computing do come from the signal processing domain, video/audio processing, mining, and so on. In general, all applications that have: 

+ Imprecision Tolerance
+ intrinsic Reliability

I.e., applications that interfere with the human perception or already are prone to errors to a certain extend. For instance, a channel decoder, like a Viterbi decoder, does not care if the bad signal quality is coming from noise on the channel, or from noise in the hardware of the transmitter.

## Research Topics

### <a name="faultinjection"></a>FPGA-Based Fault Emulation
But even if one has an application that somehow might be able to tolerate faults. We have to answer important qustions prior allowing faults.

+ How can we determine the behavior of the circuit in case of faults?
+ How can we determine where and to what extend errors cant be tolerated?

Only an extensive circuit analysis can answer these questions. This can be done with several approaches. For instance, analytically or with software-based emulations (fault-injection). They both have pros and cons, so we decided to go for third approach -> FPGA-based fault-emulation (injection). That means we are mapping the circuit we are investigating on an FPGA (although the target-platform might be an ASIC). Actually we placing it twice on the FPGA. The first copy is fault-free and in the second one we are injecting faults.Both copies run synchronously, using the same stimuli. Hence in a fault-free case they calculate the same result. However, if we now inject faults in one circuit, we can immediately observe if the fault has been propagated to the output, by observing the outputs of the two copies.

<iframe width="420" height="315" src="//www.youtube.com/embed/BwwdLG4vBSI" frameborder="0" allowfullscreen></iframe>



### <a name="dpcp"></a>Data-path Separation
coming soon

<iframe width="420" height="315" src="//www.youtube.com/embed/8VpeWYgk4-o" frameborder="0" allowfullscreen></iframe>

### <a name="globalopt"></a>Global Fault Optimization
coming soon

## <a name="publications"></a> Publications

> D. May, W. Stechele, "Improving the Significance of Probabilistic Circuit Fault Emulations", 20th IEEE International On-Line Testing Symposium (IOLTS 2014), Platja d'Aro, Catalunya, Spain, July 7-9, 2014

> D. May, W. Stechele, "Probabilistic Circuit Fault Emulation", edaWorkshop 14, Hannover, Germany, May 13-14, 2014

> D. May, W. Stechele, "A Resource-efficient Probabilistic Fault Simulator", 23rd International Conference on Field Programmable Logic and Applications (FPL 2013), Porto, Portugal, Sept. 2-4, 2013

> D. May, W. Stechele, "An FPGA-based Probability-aware Fault Simulator", SAMOS XII, International Conference on Embedded Computer Systems: Architectures, Modeling and Simulation, Samos, Greece, July 16-19, 2012

## Demos

> edaWorkshop 14, Hannover

> DATE14, Dresden

## Public Research Profiles
More information on my research as well as publications can be found on:

<a title="Follow me on ResearchGate" href="https://www.researchgate.net/profile/David_May6?cp=shp"><img src="https://www.researchgate.net/images/public/profile_share_badge.png" alt="Follow me on ResearchGate"/></a>


<a href="http://scholar.google.de/citations?user=sWB8LagAAAAJ"><img src="/img/Google_Scholar_logo.png" width="150"></a>
