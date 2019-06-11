# Modeling Short-Term Synaptic Plasticity

In this synapse we can model short-term synaptic plasticity. See [here](https://senselab.med.yale.edu/ModelDB/ShowModel.cshtml?model=168314&file=/HummosEtAl2014/pyr2pyr.mod#tabs-2) for the original file.

When a synapse is received the **NET_RECEIVE** method is called.

```
NET_RECEIVE(dummy_weight) {
    
    : t0 denotes spike time for conductance opening
    : t0 will now become the moment the spike occured
    
    t0 = t 

    : Added by Ali, Synaptic facilitation
    : In the following equations
    : tsyn is the time of the last synapse
    : tauF, tauD1, and tauD2 are rise/decay rates for 
    : facilitation, fast depression and slow depression
    : These values are set to 1 for this simulation with a min max of < 1e-9, 1e9 >
    
    F  = 1 + (F-1)* exp(-(t - tsyn)/tauF)
    D1 = 1 - (1-D1)*exp(-(t - tsyn)/tauD1)
    D2 = 1 - (1-D2)*exp(-(t - tsyn)/tauD2)
    
    : The value of the exponential will be higher when the time since the 
    : last spike is low. This will always be positive.
    : tau will determine the rate of decay, meaning 
    : if tau is large the larger effect will linger and have a greater effect
    : even if it's been a long time sinc the last spike.
    
    : With higher initial values of f, d1, and d2 the more impact each spike will have
    
    : uncomment the following line for step-by-step value output
    : printf("%g\t%g\t%g\t%g\t%g\t%g\n", t, t-tsyn, F, D1, D2, facfactor)
    
    : tsyn (time of last synapse) is set to the current time.
    
    tsyn = t

    : The "facilitation factor" is computed
    
    facfactor = F * D1 * D2
    
    
    : Effects are scaled for next spike, based on user provided input
    
    F = F * f

    if (F > 30) { 
        F=30
    }
    D1 = D1 * d1
    D2 = D2 * d2
    
    :printf("\t%g\t%g\t%g\n", F, D1, D2)
	
}
```

**BREAKPOINT** is executed at every time step. During this time the **release** method is solved using the cnexp method.

```
BREAKPOINT {

    g_ampa = gbar_ampa* facfactor
    i_ampa = g_ampa*(v - Erev_ampa)

}
```

## References 

For the complete implementation see:
* [https://github.com/tjbanks/synaptic_plasticity](https://github.com/tjbanks/synaptic_plasticity)

----   
*This page is part of a collection of pages on various topics of [computational neuroscience](https://en.wikipedia.org/wiki/Computational_neuroscience). Please direct questions and suggestions to the author Tyler Banks [[website](https://tylerbanks.net)][[github](https://github.com/tjbanks)] at [tyler@tylerbanks.net](mailto:tyler@tylerbanks.net).*
