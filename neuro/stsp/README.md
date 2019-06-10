# Short-Term Synaptic Plasticity

## General Information

Short-term synaptic plasticity (or short-term plasticity [STP]) is a phenomenon in which synaptic efficacy changes over time in response to previous presynaptic occurances. 

Two types of STP have been observed:
* **Short-Term Depression** (STD)
* **Short-Term Facilitation** (STF)

**Short-Term Depression** is caused by depletion of neurotransmitters at the axon terminal while **Short-Term Facilitation** is caused by calcium influx into the axon terminal after a spike. This increases the release probablility of neurotransmitters.

STP typically occurs on the order of hundereds to thousands of milliseconds and is temporary. Without activity the synapse will quickly return to basline levels.

STP may serve as a substrate for processing temporal information. The response of a post-synaptic neuron depends on the history of the presynaptic activity. This information could theoretically be extracted for use. STP can enrich computational studies, allowing networks to produce capabilities difficult to be seen using static connections.


## Synaptic Plasticity

The level of neural activity on the pre/post synaptic cells drives the influx of calcium ions via NMDA channels. Synaptic weight changes are driven by the level of postsynaptic Ca++ in the dentritic spine of the synapse. Low Ca++ causes weaker synapses while higher levels cause synapses to strengthen. The level of Ca++ drives the AMPA efficacy.

There are 5 steps that drive changes in AMPA efficacy. Both NMDA channels and Ca++ play critical roles. Ca++ sets of a series of reactions that ends up controlling how many AMPA recptors are functional at the synapse. The 5 steps are as follows:

1. Postsynaptic membrane potential (Vm) has been elevated as a result of all synapstic input and more importantly the **backpropagatic action potential**. Backpropagating action potentials are facilitated by active Na+ channels along the dentrites. 
1. The higher Vm causes magnesium ions (Mg+) to be repelled out of the NMDA channels, unblocking them.
1. The presynaptic neuron fires an action potential, releasing glutamate into the synaptic cleft.
1. Glutamate binds to the NMDA receptor, allowing Ca++ to flow into the postsynaptic cell. Again, this only occurs when VM is higher and Mg+ has been repelled.
1. A higher concentration of Ca++ causes second messenger systems that result in changes in AMPA receptor efficacy, or the number of active AMPA channels in the postsynaptic cell. Thus changing the synaptic weight.

Although a weaker contributor, Ca++ can also enter via voltage-gated Ca++ channels (VGCC's), depending only on Vm levels.

Metabotropic glutamate receptors (mGlu) can also facilitate synaptic plasticity. mGlu directly triggers chemical reactions when a neurotransmitter binds to them. The reactions can then modulate changes in AMPA receptors triggered by Ca++.


## References
* [https://www.ncbi.nlm.nih.gov/pubmed/11826273](https://www.ncbi.nlm.nih.gov/pubmed/11826273)
* [http://www.scholarpedia.org/article/Short-term_synaptic_plasticity](http://www.scholarpedia.org/article/Short-term_synaptic_plasticity)
* [https://mcb.berkeley.edu/labs/zucker/PDFs/Zucker_AnnuRevNeurosci12,13.pdf](https://mcb.berkeley.edu/labs/zucker/PDFs/Zucker_AnnuRevNeurosci12,13.pdf)
* [https://grey.colorado.edu/CompCogNeuro/index.php/CCNBook/Main](https://grey.colorado.edu/CompCogNeuro/index.php/CCNBook/Main)


----   
*This page is part of a collection of pages on various topics of [computational neuroscience](https://en.wikipedia.org/wiki/Computational_neuroscience). Please direct questions and suggestions to the author Tyler Banks [[website](https://tylerbanks.net)][[github](https://github.com/tjbanks)] at [tyler@tylerbanks.net](mailto:tyler@tylerbanks.net).*
