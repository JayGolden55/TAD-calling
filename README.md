# TAD-calling
## What are TADs?

TADs are called topology-associated domains. TADs were first discovered on low-resolution mammalian Hi-C contact frequency heatmaps in 2012. Several research groups found that the contact frequency heatmaps could be clustered into megabase-scale blocks where the DNA sequences exhibit significantly higher interaction frequency with other DNA sequences within the domain than those outside of the block [1]. The empirical block structures on the heatmap were defined as TADs. The size of a TAD varies from 100kb to several megabases.

## Why are TADs important?

DNAs were long believed to be mingled and intertwined in the nucleus like a bowl of spaghetti. However, the Hi-C contact frequency maps revealed more organized chromatin structures on different scales, including TADs. 

The majority of observed interactions between promoters and enhancers do not cross TAD boundaries [2]. Removing a TAD boundary can form new promoter-enhancer contacts. It has been proposed that TADs constitute functional units in the genome, important for the correct regulation of gene expression. TADs co-localize regulatory elements with their target genes, and are thought to promote co-regulation of the genes they contain, creating “gene regulatory domains” [3]. Disrupted TAD boundaries are associated with diseases, such as cancer.

Divergent CTCF sites were found to be enriched at TAD boundaries. One of the proposed mechanisms for the formation of TADS was loop extrusion. In this mechanism, cohesins extrude DNA loops until encounter divergent CTCF sites [4]. DNA sequences on the loop self interact more than interacting with sequences out of the loop. 

![alt text](https://github.com/Beijia-Yuan/TAD-calling/blob/main/final-image1.jpg)
*CTCF binding sites and chromatin marks enriched at TAD boundaries [6] and a model for loop extrusion and extrusion-based chromosome organization [4]*

Recent studies in single-cell Hi-C and high-resolution microscopy data revealed that TAD-like structures were also present on the single-cell level. However, the TAD-like structures are highly variable from cell to cell, with a non-zero boundary probability across the genome. Moreover, single-cell level TAD-like structures were observed in cohesion-depleted cells whereas ensemble-averaged TAD structures disappeared in bulk Hi-C data [5]. This indicated that loop extrusion is not sufficient to explain TAD formations. Other mechanisms such as thermodynamic models of phase separations were proposed. 

![alt text](https://github.com/Beijia-Yuan/TAD-calling/blob/main/final-image2.JPG)
*image_caption*

In summary, understanding the formation and effects of TAD structures will help us understand chromatin dynamics and gene regulations, and potentially provide insights into treatments of diseases.

## References

[1] Beagan, J.A., Phillips-Cremins, J.E. On the existence and functionality of topologically associating domains. Nat Genet 52, 8–16 (2020). https://doi.org/10.1038/s41588-019-0561-1

[2] Whalen, S., Truty, R. M., & Pollard, K. S. (2016). Enhancer-promoter interactions are encoded by complex genomic signatures on looping chromatin. Nature genetics, 48(5), 488–496. https://doi.org/10.1038/ng.3539 

[3] Long, H.S., Greenaway, S., Powell, G. et al. Making sense of the linear genome, gene function and TADs. Epigenetics & Chromatin 15, 4 (2022). https://doi.org/10.1186/s13072-022-00436-9 

[4] Banigan, E. J., & Mirny, L. A. (2020). Loop extrusion: theory meets single-molecule experiments. Current opinion in cell biology, 64, 124–138. https://doi.org/10.1016/j.ceb.2020.04.011 

[5] Conte, M., Fiorillo, L., Bianco, S. et al. Polymer physics indicates chromatin folding variability across single-cells results from state degeneracy in phase separation. Nat Commun 11, 3289 (2020). https://doi.org/10.1038/s41467-020-17141-4 

[6] Barrington, C., Georgopoulou, D., Pezic, D. et al. Enhancer accessibility and CTCF occupancy underlie asymmetric TAD architecture and cell type specific genome topology. Nat Commun 10, 2908 (2019). https://doi.org/10.1038/s41467-019-10725-9
