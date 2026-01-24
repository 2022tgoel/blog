
* There are 64 codons ($4^3$) for 20 amino acids. Naturally, this means that there is a lot of redundancy in which codons correspond to which amino acid. Methionine is an interesting amino acid because it only has one codon, and that codon is also the start codon. There are two tRNA sequences for methinione, one of which is recognized by the initiation complex and is used to start translation, and the other is the regular methionine tRNA. Methionine increases the availability of charged Met-tRNA.  This is why methionine restriction (methionine is more prevalent in animal-based protein sources than plant-based sources) is often linked to longevity (e.g. https://pmc.ncbi.nlm.nih.gov/articles/PMC5008916/) -- high methionine levels encourage continuous protein synthesis and activate mTOR / growth signaling pathways. 

* https://www.youtube.com/watch?v=mMl9eHC4kyA -- this is a really good video that disambiguates a lot of what people usually mean when they say something is "anti-inflammatory" (usually that it just has a bezene ring somewhere / can stably harbor a radical) and why ROS are bad. 
	* For example there are some people (usually not scientists) who think cardio is bad for you. Basically the reason they think that is because it will cause acute oxidative stress through the leakage of elections that react with $O_2$ to produce superoxide (This is $O_2$ with an electron). 


* **Rapamycin**: This mainly affects the mTOR / growth signaling pathways, which are linked to cancer (mTOR is frequently overactive in cancer). So it has an affect on reducing the change of cancer by reducing the rate of cell division in a similar nature to CR.  Rapamycin is not an endogenous metabolite that goes down with age (the case of [taurine](https://www.science.org/content/blog-post/taurine)), but rather a hack to crank up pathways that have effects that we mostly want
* AMPK is the opposite of mTOR, activated by a high **AMP/ATP ratio**



Cardiovascular Disease, Cancer, and Neurodegenerative diseases are the big three dominant causes of death in long-lived populations. 


## Hallmarks of Aging

### Primary Hallmarks

###### Aside: Which cells matter? 
Aging becomes system-limiting when stem cells accumulate telomere attrition and genomic instability. Damage in differentiated cells matters too, but it’s usually replaceable until the stem-cell compartment itself is compromised.

Post-mitotic cells complicate the picture a bit, because they cannot be replaced. Thus, neurodegeneration and cardiac aging depend more on cell-intrinsic damage. 

#### Genomic instability
replication errors, and damage due to interactions with ROS

#### Telomere attrition

###### How many times do stem cells divide?
| Stem cell type                   | Estimated divisions                             |
| -------------------------------- | ----------------------------------------------- |
| Hematopoietic stem cells (blood) | ~1,000–10,000                                   |
| Intestinal stem cells            | thousands                                       |
| Skin stem cells                  | thousands                                       |
| Muscle satellite cells           | hundreds–thousands                              |
| Neural stem cells                | hundreds                                        |
| Germline stem cells              | Effectively indefinite (species survival scale) |
###### How many times do somatic cells divide? 

| Cell type              | Divisions                  |
| ---------------------- | -------------------------- |
| Fibroblasts            | 40–60 (Hayflick limit) |
| Epithelial progenitors | 10–50                  |
| Immune effector cells  | 10–30                  |
| Hepatocytes            | 20–40                  |
| Neurons                | 0                      |
| Cardiomyocytes         | ~0–1                   |

###### If telomere shortening was the only cause of aging, how long would we live? 
This estimated lifespan of 200–500 years. **TODO**: add a source.

#### Epigenetic Alterations
Carefully arranged set of DNA and histone methylations and chromatin coiling becomes disrupted with age, leading to irregular levels of gene activity. A pattern that seems associated with aging is a generalised loss of methylation.
#### Loss of Proteostatis
Protein homeostasis is the state of a cell when the concentrations of proteins is the right one for cell function, and when deviations from it can be returned to equilibrium by the cell through various mechanisms such as proteins that help other proteins fold themselves properly (chaperones like _heat shock proteins_ ), or degradation of incorrectly folded proteins in lysosomes or proteasomes.

### Antagonistic Hallmarks
1. Deregulated nutrient sensing
2. Mitochondrial dysfunction
3. Cellular senescence
###### Why is senesence bad? 
A senescent cell resists apoptosis, remains metabolically active, and secretes inflammatory factors. This causes chronic inflammation, and can induce senescent in nearby cells. Senescence is what happens when a cell is too dangerous to divide but too valuable to kill. Aging is what happens when too many such cells accumulate.

###### What decides senescence vs apoptosis? 
The severity and type of damage (more severe = apoptosis), p53 signaling dynamics, cell type, mitochondrial state, and tissue context.

### Integrative Hallmarks

1. Stem Cell Exhaustion
2. Altered intracellular communication

###### What causes stem cell exhaustion?
Telomere shortening, Genomic instability, Epigenetic drift, Mitochondrial dysfunction... basically a bunch of the stuff above. 

Without stem cells, every tissue cell would need infinite replication, and the cancer risk would be enormous. 

 
## Tissue Reprogramming, Embryonic Development, and Related

A PSC (pluripotent stem cell) is an embryonic stem cell. If you induce it, you get a **teratoma**, which a tumor originating from germ cells. Like, they try to make an embryo in your body! This is why returning cells to age 0 is not actually a good idea. 

#### Aside: Embryos

There are three major germ lines that are form: the **endoderm**, which becomes the epithelial lining of the gut, the pharynx, the esophagus, the stomach, the liver, the lungs, the thyroid, and a bunch of other stuff. The **mesoderm**, which becomes the bone, cartilage, circulatory system, lymphatic system, dermis, and a bunch of other stuff! Then there is the **ectoderm**, which is the hair, nails, epidermis of the skin, lens of the eye, tooth, and a bunch of this other auxiliary stuff. 

![[Pasted image 20260109092355.png]]


Rejuvenate bio have shown that expressing OKS (M is an oncogene) in mice leads to an extended lifespan. 

#### Machine Learning Tech

Previously, people were using epigenetic clocks that operated on a petri dish of cells. A new technique was trained to predict methlyation age from the data of a *single cell* using machine learning. 

A *virtual cell* is a transformer/GNNs that has been fed a bunch of transcriptomes. You can alter the expression of a few genes and view the downstream impact of the rest of the genome. How is this technique able to distinguish causality? I actually have no idea. 


SB000 is a single gene that reverses aging in fibroblasts and is safer. 

### Papers
* https://pubmed.ncbi.nlm.nih.gov/40950238/ 

* https://www.cell.com/cell/abstract/S0092-8674(25)00853-0