### Types

* Stem cells: cells that can self-renew and differentiate
	* Stem cells can divide for very long periods because they are actively protected at multiple biological levels. 
		* Stem cells express telomerase
		* Stem cells divide *asymmetrically*. One daughter remains a stem cell, one daugher differentiates. Damaged proteins and old mitochondria are preferentially shunted into the differentiating cell. 
* Germ cells: for reproduction
* Somatic cells: all non-germline cells of the body — including stem cells, progenitors, and fully differentiated cells
	* Actively dividing somatic cells: These replicate frequently, but only for a limited time
		* Skin keratinocytes, Gut epithelial cells
			* The skin and gut epithelia actually function very similarly, with some of the fastest renewal rates in the body (gut epithelium is actually the fastest, around 4 days, while the skin is 2-4 weeks), and stem cells at the bottom
		* Blood progenitors
	* **Quiescent** / conditionally dividing cells: These divide *only after injury*
		* Liver cells
		* Endothelial cells
		* Fibroblasts: secrete - collagen, elastin, proteoglycans to maintain the extracellular matrix.
	* **Post-mitotic cells**: do not replicate. They must come from stem cells. 
		* Neurons
		* Cardiomycocytes: is a heart muscle cell responsible for contracting to pump blood
		* Skeletal muscle
###### Why is telomerase turned off for non-stem cells? 
If telomerase stays on, cells can divide indefinitely. Cells with active telomerase are **replicatively immortal**. This means that they can accumulate replication errors and epigentic alterations indefinitely. Telomere shortening acts as a division counter, and after the cell has replicated to a certain limit, it becomes senescent. This creates **replicative senescence**, a powerful tumor-suppressive mechanism. 

Mice have longer telomeres, more telomerase activity, thus they die young and get cancer very easily.

Also, dna repair mechanisms don't work on the telomeres, so they can accumulate mutations more easily. 

## Components

* **nucleus**
* **Golgi apparratus** packages proteins and lipids from the endoplasmic reticulum (ER) into vesicles for secretion or delivery to other organelles like lysosomes
* **ER** which is both smooth (no ribosomes) and rough (has ribosomes). The ribosomes on the ER are for sending the protein outside the cell, while the free ribosomes make proteins that stay in the cytoplasm or enter one of the organelles. Actually there is a signaling sequence (called the **signal peptide**, a ~20 amino acid polypeptide) that causes a free ribosome to be bound while it is generating the protein. SRP, or **signal recognition particle**, triggers the binding.
* **peroxisome**: fatty acid metabolism, detoxification of harmful reactive oxygen species
* **mitochondria**: carbohydrate metabolism

## Trafficking
* 50% of proteins don't stay in the cytosol. This is a lot!

1. Using targeting sequences -- part of the protein sequence
	1. Nuclear pores: large openings plugged by some protein. **nuclear localization sequences** that are positively charged (lysine/arginine). NLS binds to escort protein importin
2. Post translational modifications. The advantage is that you don't have to make a new protein de novo (slow!), you can just take advantage of existing stores. 
	1. Lipidation: Add a hydrophobic lipid tail to the protein which causes it to go to the plasma membrane.
	2. Phosphorylation
	3. Ubiquitination: for misfolded proteins
		1. Ubiquitin is 76 amino acids 
		2. proteasome: shredded that chops proteins in small peptides that are 8-14 amino acids in length. 
			1. first unfolding, then protease activity
## Division
* The chromosome becomes **replicated** and **condensed**
	* It has a **centromere** which is surrounded by proteins which form the **kinetochore**
* The **microtubules** are assembling (push) and disassembling (pull) parts of the **cytoskeleton**
	* These pull apart by the chromosome by attaching to the kinetochore
## Signaling
Where did the signal come from: 
* **Autocrine**: Same cell
* **Juxtracrine**: Cell contact dependent (even closer than paracrine)
* **Paracrine**: Nearby cell
* **Endocrine**: Distant cell

Steroid are very nonpolar so then tend to be able to directly cross the cell membrane. Other signals typically need to rely on transduction. 

Membrane proteins are **50% of the important drug targets**. Also, most drugs are inhibitors. 

1. G protein coupled receptors. 7 Transmembrane helices.
2. Receptor tyrosine kinases (RTK)
3. Ion Channels

What is a G-protein? It is something than binds to GDP (guanine di-phosphate) or GTP (guanine tri-phosphate). When bound to GDP, its inactive, when its bound to GTP, it is active. They bind to the phosphates, so GTP is a tighter state. 

These G-proteins can either be monomeric, or trimeric, in which case they have three subunits ($\alpha, \beta, \gamma$). 

When the ligand binds to the receptor, that initiates the functional change in the G-protein from the inactive to the active state. 

You can also have signaling pathways that cause a *transcription factor to bind to a protein*, causing a transcription of a gene to occur. 

#### Phosphorylation
Adds a phosphate group to the oxygen on the -OH group of an amino acid (e.g. tyrosine). A **kinase** makes this modification. **Phosphotase** does the reverse reaction. 

Kinases do _not_ universally need phosphorylation to function. Phosphorylation is one of several activation mechanisms. In RTK signaling, phosphorylation is crucial not mainly to turn kinases on, but to create information-carrying docking sites and amplification. RTKs usually have very low basal activity before phosphorylation.

When a ligand binds to RTK, this triggers a pair of RTKs to dimerize and phosphorylate each other. This is necessary because a kinase works much better on another protein than on itself, and it needs to be in close enough proximity to the other protein for the mechanism to be activated (which dimerization achieves). 

## Cell Cycle

G1, S (Synthesis, DNA replication), G2, M (mitosis, cell division)

###### What are the main mechanisms for initiating cell division?

**Cyclins**, which are are regulatory proteins that bind to and activate cyclin-dependent kinases. CAKs are CDK-activating kinases. RTK signaling induces cyclin gene expression, and therefore is an upstream regulator of this whole process. 
![The ordering of the two universal steps in CDK activation is ...](https://images.openai.com/thumbnails/url/47jWQ3icu5mVUVJSUGylr5-al1xUWVCSmqJbkpRnoJdeXJJYkpmsl5yfq5-Zm5ieWmxfaAuUsXL0S7F0Tw5OTcoMCLTM8XNOSU1KD483tCyxrCwLNC0pcS3Kco4v9MsKDU2yDLBITkor9izKLTVKUSsGAJJBJyc)
###### What are the main mechanisms for regulating the cyclins?
Ubiquitination
###### How can you check if a mutation disrupted cell division? 
In budding yeast cells, you can check the proportion of cells in each phase. There is an expected distribution based on how lnog each stage is
###### What is the evidence that there is a checkpoint in the G2 phase? 
Usually, a cell when exposed to radiation during the S phase, has a longer G2 phase followed by an M phase that produces two healthy cells. When a mutation at Rad-9 was introduced, the G2 phase was short and the cells produced die. This suggests that Rad-9 regulates the G2 checkpoint that checks that DNA replication happened correctly. 


## Stem Cells

Tissue Homeostasis: renewal = death

Adult stems cells -- **multipotent**. associated with a specific organ

There are also **pluripotent stem cells**, which can give rise to multipotent stem cells. 

If you start with a stem cell, you can generate an entire organ in a dish. 