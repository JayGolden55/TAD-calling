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
*Bulk and single-cell Hi-C contact frequency heatmap for normal and cohesin-depleted cells. TAD-like structures showed a high variablility from cell to cell. In cohesin-depleted cells, TAD structures disappeared on the ensemble average level, but were preserved in single cells. [5]*

In summary, understanding the formation and effects of TAD structures will help us understand chromatin dynamics and gene regulations, and potentially provide insights into treatments of diseases.

## Finding TADs in Hi-C Maps

### Theoretical Basis
![alt text](https://github.com/JayGolden55/TAD-calling/blob/main/tad_domains.png)
*Relationship between Hi-C contact matrix elements and structural elements of chromatin []*

All methods for determining TADs attempt to locate regions in which multiple contacts between genomic regions
occur that are otherwise isolated from other regions containing distal genomic contacts. On a Hi-C map, this can be seen
as a checkered board, in which the total region is the TAD, isolated from other high contact frequency regions, and each individual
checkered square indicates a high contact interaction between two distal genomic regions. A good algorithm for accurately 
determining TADs from a Hi-C map should be able to both determine all highly contacted regions and determine the borders
between isolated regions to accurately showcase real compartments in the chromatin structure. Since TADs vary in size  
and number of sub-compartments, approaches to categorize often face various challenges specific to the region being analyzed,
with different algorithms having greater or worse success depending on the area of interest. Approaches vary in their use
of computational techniques, with some centered around probabilistic computations, others utilizing HMMs, and others 
utilizing clustering based approaches.

## Some approaches

### Arrowhead Matrix
![alt text](https://github.com/JayGolden55/TAD-calling/blob/main/arrowhead_mat.png)
*Transformation of contact map to arrowhead matrix []*


Transformation of the Hi-C contact map to an arrowhead matrix gives a probabilistic estimate of the likelihood a region is within
a TAD. For every position in the matrix $i,i+d$ where $d$ is some predefined distance, the value in the arrowhead matrix is computed as
$$A_{i,i+d}=\frac{M_{i,i-d}-M_{i,i+d}}{M_{i,i-d}+M_{i,i+d}}=1-\frac{2*M_{i,i+d}}{M_{i,i+d}+M_{i,i-d}}$$
Where $A_{x,y}$ is the value of the position $x,y$ in the arrowhead matrix and $M_{x,y}$ is the value of the position $x,y$ in the contact
matrix. This can be understood as the observed contact frequency over the expected contact frequency based on the related positions. If the value is high
the observed contact frequency cannot be reasonably explained by the related region, implying the relationship is significant and that the position of interest
is within a TAD. Once the transformation is applied to the entire matrix, high positive "arrows" indicate the region is 
within a TAD and are kept isolated from other regions.

### Clustering
![alt text](https://github.com/JayGolden55/TAD-calling/blob/main/clusters.png)

*Contacts from Hi-C contact map, shown on right, are associated with specific clusters with different likelihoods []*

As the output of a Hi-C analysis is the locations of high-contact frequency regions, a TAD can be thought of as a collection of closely
related regions, making clustering a reasonable approach to organizing the contacts. K-means clustering attempts to group the 
contacts to contacts that are distally close in euclidean distance across the Hi-C map. This approach faces difficulties because
it is often unclear how many TADs should belong to a region and does not isolate specific regions well.
In recent years, TADs have been found to be defined more directly by hierarchical levels of organization rather than explicitly disjoint
compartments. Hierarchical clustering has been found to capture this organization well by grouping levels of relationship rather
than isolated regions. This method groups the closest contacts together into levels, and then continuously groups levels into higher order levels.
In this way, depending on the study being conducted, a researcher can specify the level of compartmentalization they are looking at 
by which level of clustering they want to examine.



## References

[1] Beagan, J.A., Phillips-Cremins, J.E. On the existence and functionality of topologically associating domains. Nat Genet 52, 8–16 (2020). https://doi.org/10.1038/s41588-019-0561-1

[2] Whalen, S., Truty, R. M., & Pollard, K. S. (2016). Enhancer-promoter interactions are encoded by complex genomic signatures on looping chromatin. Nature genetics, 48(5), 488–496. https://doi.org/10.1038/ng.3539 

[3] Long, H.S., Greenaway, S., Powell, G. et al. Making sense of the linear genome, gene function and TADs. Epigenetics & Chromatin 15, 4 (2022). https://doi.org/10.1186/s13072-022-00436-9 

[4] Banigan, E. J., & Mirny, L. A. (2020). Loop extrusion: theory meets single-molecule experiments. Current opinion in cell biology, 64, 124–138. https://doi.org/10.1016/j.ceb.2020.04.011 

[5] Conte, M., Fiorillo, L., Bianco, S. et al. Polymer physics indicates chromatin folding variability across single-cells results from state degeneracy in phase separation. Nat Commun 11, 3289 (2020). https://doi.org/10.1038/s41467-020-17141-4 

[6] Barrington, C., Georgopoulou, D., Pezic, D. et al. Enhancer accessibility and CTCF occupancy underlie asymmetric TAD architecture and cell type specific genome topology. Nat Commun 10, 2908 (2019). https://doi.org/10.1038/s41467-019-10725-9

Zufferey, M., Tavernari, D., Oricchio, E. et al. Comparison of computational methods for the identification of topologically associating domains. Genome Biol 19, 217 (2018). https://doi.org/10.1186/s13059-018-1596-9

Rao, Suhas S P et al. “A 3D map of the human genome at kilobase resolution reveals principles of chromatin looping.” Cell vol. 159,7 (2014): 1665-80. doi:10.1016/j.cell.2014.11.021

