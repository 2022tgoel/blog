* A **plasmid** is a circular double-stranded DNA molecule. Plasmids are transcribed by the host cell’s machinery, because plasmids contain bacterial promoters. Chromosomes hold essential genes for survival and replicate with the cell, while plasmids are smaller, extrachromosomal DNA loops, often circular, carrying non-essential but advantageous genes (like antibiotic resistance).
* A **vector** is a plasmid designed to carry foreign DNA. If you just inject a piece of foreign DNA into a cell, it usually gets degraded and doesn't replicate
* **restriction enzyme**/**restriction endonuclease**: for opening the plasmid so you can insert the gene . You have to make sure that your restriction enzyme only recognizes one piece of the plasmid. 
* **pBR322**: is a very successful specific plasmid. 
* **ORI**: origin of replication
* **ROP**: repressor of primer. encodes a protein that regulates plasmid copy number. when it decides to stopit codes for a protein that blocks off the ORI. 
* **selectable markers** (e.g., ampicillin resistance gene) help us distinguish between cells with the plasmid and cells without the plasmid. 

## AAV

This is a totally different way of delivering genes from a plasmid. 

AAV is produced in cells (usually HEK293) by **co-transfecting plasmids**. 

**Plasmid 1 — the transfer vector**

contains the gene of interest: `ITR — promoter — gene — polyA — ITR`

**Plasmid 2 -- rep/cap**

Rep proteins bind ITRs, then interacts with the inner surface of assembling capsids and threads the ssDNA (single stranded DNA) into the capsid. 

AAV capsids are non-enveloped icosahedral shells (~25 nm). They are made from proteins **VP1**, **VP2**, and **VP3**.

Small amino-acid differences in capsids determine which tissues are infected.

 **Plasmid 3 — helper**

Supplies adenoviral helper functions

The capsid size is relatively constrained. Increasing capsid size would require new protein–protein angles, new curvature, and new interfaces. This is why there is a 4.7 KB of DNA size limit. 

### CRISPR

> People have an interesting (to us) attitude towards genetic inequity. They often just accept that some people only need 4-6 [hours](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2884988/) [of](https://www.science.org/doi/10.1126/scitranslmed.aax2014) [sleep](http://cell.com/neuron/fulltext/S0896-6273\(19\)30652-X) with [seemingly no downsides](https://gwern.net/doc/www/www.thecut.com/0eb14a4e529541bc6bb8f9804d684f38efa7b27f.html) (even accounting for pleiotropy) besides hyperactivity, others are nearly [immune to Alzheimer’s](https://nintil.com/what-is-alzheimers#:~:text=Additionally%2C%20people%20with%20the%20so%20called%20Icelandic%20mutation%20\(or%20A673T%2C%20an%20alanine%20to%20threonine%20replacement%20at%20position%20673%20in%20APP\)%20don%27t%20develop%20Alzheimer%27s%2C%20perhaps%20because%20the%20conformation%20of%20APP%20resulting%20from%20the%20mutation%20makes%20BACE1%20cut%20preferentially%20at%20the%20%CE%B2%E2%80%B2%20site%2C%20which%20is%20not%20amyloidogenic) or [heart disease](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5976255/#R5), or use [oxygen](https://www.pnas.org/doi/abs/10.1073/pnas.1700527114) [much more efficiently](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC46538/pdf/pnas01462-0175.pdf), among [many other examples](https://arep.med.harvard.edu/gmc/protect.html) and even bristle at the idea that we should make these traits more widely available. While we agree it’s important to discuss the implications, we see the kneejerk anti- response as a status quo bias, especially since soon things won’t have to be this way.

https://stephenmalina.com/post/2023-06-07-editing-part-i/


The vector in this case encodes the genes for a few different things, including:
- **Cas nuclease** (e.g., Cas9) → cuts DNA
- **Guide RNA (gRNA)** → tells Cas9 _where_ to cut. 
- This is different from classical restriction endonucleases, where they are hardwired to cut a a specific spot.

* Then, there is a separate component that uses DNA's repair pathway, specifically Homology Directed Repair

Note that plasmids in eukaryotes die out eventually


## Ligation

When a resitriction endonuclease makes a cut in a plasmid, it leaves "sticky ends". If these match a foreign DNA (because the DNA was processed using the same restriction enzyme) than it will bind to it and the foreign DNA will be incorporated in. However, the phospates and hydroxlys where the foreign dna and the orignal plasmid won't be bonded. DNA ligase creates the phosphodiester bond. 

**Functional Complementation**: Take a cell that is defective in some function and restore the phenotype through plasmid injection.