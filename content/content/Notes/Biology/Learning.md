
### Definitions

Explicit (or declarative) memory involves two classes of knowledge: episodic memory, which represents personal experiences, and semantic memory, which represents general knowledge and facts. Implicit memory includes forms of perceptual and conceptual priming, as well as the learning of motor and perceptual skills, perceptual regularities, and reinforced habits.

**Priming** is the automatic influence of exposure to one cue on processing of a later cue. *Conceptual priming* provides enhanced access to task-relevant semantic knowledge because that knowledge has been used before. It is correlated with decreased activity in left prefrontal regions that subserve initial retrieval of semantic knowledge. In contrast, *perceptual priming* occurs within a specific sensory modality and depends on cortical modules that operate on sensory information about the form and structure of words and objects.

Implicit memory can be **associative**, where the brain learns the relationship between two stimuli. Like priming. It can also be **non-associative**. **Habituation** is a decrease in a response that occurs when a benign stimulus is presented repeatedly. **Sensitization** (or pseudo-conditioning) is an enhanced response to a wide variety of stimuli after the presentation of an intense or noxious stimulus. For example, an animal will respond more vigorously to a mild tactile stimulus after receiving a painful pinch.

The hippocampus is in the medial temporal lobe, a specific region (though the whole medial temporal lobs is important) for storing episodic memories. ***Consolidation* processes stabilize stored representations, rendering explicit memories less dependent on the medial temporal lobe**. This seems like an extremely important mechanism. 

*Classical conditioning* is the formation of a predictive relationship between two stimuli (**pretraining**), *operant conditioning* can be considered as the formation of a predictive relationship between an action and an outcome (**RL**).

Motivationally significant events are prioritized in memory through the enhancement of encoding, storage, and consolidation processes.
### Channels
In general, the calcium and sodium concentrations are higher outside the neuron, and the potassium concentration is high inside the neuron. This is why sodium and calcium will rush in when the ion channels open. 

### Neurons
##### Ionotropic receptors
The receptor **is** the ion channel.
- Acetylcholine → nicotinic ACh receptor
- Glutamate → AMPA / NMDA receptors
- GABA → GABA_A receptor

GABA and glutamate are the fast transmitters. 

##### Metabotropic receptors
Neurotransmitter does not open a channel directly -- receptor activates a G protein. 
- Dopamine receptors
- Muscarinic acetylcholine receptors
- GABA_B receptors
- Serotonin

These are more of the *neuromodulators*, shaping network excitability, plasticity, and brain state. 

### Habituation

In *homosynaptic depression*, every time a sensory neuron is fired, it releases less neurotransmitter, triggers the postsynaptic neurons / pathway less. Long-term habituation is caused by a decrease in the number of synaptic contacts between sensory and motor neurons.

### Sensitization

1. serotonin released from the interneurons
2. serotonin binds to a G protein-coupled receptor
3. This increases the activity of adenylyl cyclase
4. The activates cyclic adenosine monophosphate (cAMP) (conversion ATP --> cAMP)
5. cAMP activates cAMP-dependent protein kinase (PKA)
6. protein phosphorylation mediated by PKA and PKC enhances the release of transmitter from sensory neurons
	1. PKA phosphorylates the K+ channel, causing it to close
### Conditioning

With conditioning, the response can be even stronger than the response from sensitization. Why? Because when a sensitization response follows an action potential from a previous reaction, then Ca2+ has recently bound to the adenyl cyclase, which increases its activity and strengthens the whole signaling response. 

![[Screenshot 2026-01-09 at 11.40.59 AM.png]]

### Consolidation

Repeated activation of the sensitization / conditioning pathways leads to a steady rise in cAMP. This triggers a cascade that causes transcription factor CREB-1 to be activated, which binds to promotor region CRE. One gene activated by CREB-1 encodes a ubiquitin hydrolase, a component of a specific ubiquitin proteasome that leads to the proteolytic cleavage of the regulatory subunit of PKA, resulting in persistent activity of PKA, even after cAMP has returned to its resting level. CREB-1 also activates the expression of the transcription factor C/EBP, which leads to expression of a set of unidentified proteins important for the growth of new synaptic connections

![[Screenshot 2026-01-09 at 4.42.50 PM.png]]
![[Screenshot 2026-01-09 at 4.43.18 PM.png]]


How are only specific synapses targeted by this change in the epigenetic state of the cell? Well, there was an experiment where a researcher took a sensory neuron with two terminal synapses. They gave one synapse five pulses of serotonin, which is enough to facilitate long-term memory at that synapse (but left other other synapse unchanged!). However, if they also gave *one* pulse of serotonin at the other synapse, both got long term growth. The large dose at one synapse *did* affect the other synapse. This means that there is some kind of binary marking mechanism of which synapses had activity. This process is called synaptic capture/tagging. 

### Long-Term Potentiation

Long-term potentiation in the lateral nucleus of the amygdala is triggered by Ca2+ influx into the postsynaptic neurons in response to strong synaptic activity. The Ca2+ entry is mediated by the opening of both N-methyl-d-aspartate (NMDA)-type glutamate receptors and L-type voltage-gated Ca2+ channels in the postsynaptic cell. Because NMDA receptors are normally blocked by extracellular Mg2+, they require a large synaptic input to generate enough postsynaptic depolarization to relieve this blockade. They also obviously need the glutamate from the presynaptic neuron firing. 


#### Hippocampus


![[Screenshot 2026-01-11 at 8.45.52 AM.png]]


There are two pathways to CA1, one indirect and one direct pathway. 

* LTP at the mossy-fiber pathway is largely presynaptic (driven by Ca2+ influx at the presynaptic terminals) and therefore non-associative (doesn't depend on the postsynaptic neuron firing)
* At the schaffer collateral pathway, LTP is associative, relying on the NDMA receptors
* The direct pathway uses NDMA receptors and L-type voltage-gates Ca2+ channels
* The AMPA receptor is the one that starts the action potential at the postsynaptic neuron. However, it some cases, there are "silent synapses," which work when the postsynaptic neuron is depolarized, because this means that the NDMA receptor is unblocked. There are only NDMA receptors at the postsynaptic neuron, not AMPA receptors. At these synapses, adding AMPA receptors results in a strong strengthening of the response. 
* The NDMA pathway builds new AMPA receptors. This increases its response to glutamate. It also sends signals to the presynaptic neuron to release more glutamate. 
* Late LTP is what uses CREB and gene transcription to recruit new proteins

![[Screenshot 2026-01-11 at 9.04.21 AM.png]]

### Long Term Depression
There are two mechanisms that cause this
1. A long low-frequency stimulation
2. A "reverse" pathway, where the postsynaptic neuron depolarizes right before the presynaptic neuron release glutamate

A low-frequency tetanus basically lets it a significantly smaller amount of Ca2+ through the NDMA receptor. This is not enough to activate the same molecules that are involved in LTP, but a different set of molecules that have a higher affinity for Ca2+.

### Random Facts
* in the nematode C. elegans, every individual has exactly 302 neurons, and they’re always in the same place and connected the same way
* Neural firing is energetically expensive — it’s much cheaper to transmit signals via releasing chemicals which travel diffusively! However, diffusive signaling spreads only as distance ~ time^1/2, which ends up meaning it’s usually not a good choice when you need to go, say, more than a millimeter in one direction. Chemical computing tends also to require fewer parts and take up less space.

### GABA switch

* GABA is a neurotrasmitter for Cl- channels
* In the beginning, Cl- concentration is higher inside the neuron, so GABA triggers an *excitatory* response. 
* Later on, Cl- concentrations in the outside become larger, so GABA triggers an *inhibitory response*.
* Early brains need excitation and synchrony to wire themselves up in the beginning; mature brains need inhibition and precision to compute

## Brains automatically perform probabilistic computation

https://www.hms.harvard.edu/bss/neuro/bornlab/nb204/final_exam/YangShadlen2007.pdf

Experiment setup:
* Monkey
* You show them 4 shapes from a set of 10.
* There are two options to pick from, red or green. The log-odds of the options are given by $\sum_i w_i$, where each shape has weight $w_i$. 
* So in total, there are ${10 \choose 4} + 3 * {10 \choose 3} + 3 * {10 \choose 2} + {10 \choose 1} = 715$ total inputs / log-odds they could come to. This is way too much to memorize. 

If the sum of weights $w$ is the log-odds, then $P(\text{red}) = \frac{e^w}{1 + e^w}$   

![[Screenshot 2026-01-21 at 1.07.24 PM.png]]'

Amazingly, the monkeys intuitively learn this logistic function:

![[Screenshot 2026-01-21 at 1.09.26 PM.png]]


The parietal lobs has spatially selective persistent activity. Basically, there are one set of neurons that fire when you plan of move you eyes in one direction, and another set of neurons when you plan to move your eyes in a different direction. The firing rate of these neurons also depends on log odds (linearly) and this is outside of the final decision made by the monkey. 