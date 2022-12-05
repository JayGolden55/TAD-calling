# TAD-calling
## What are TADs?

TADs are called topology-associated domains. TADs were first discovered on low-resolution mammalian Hi-C contact frequency heatmaps in 2012. Several research groups found that the contact frequency heatmaps could be clustered into megabase-scale blocks where the DNA sequences exhibit significantly higher interaction frequency with other DNA sequences within the domain than those outside of the block [1]. The empirical block structures on the heatmap were defined as TADs. The size of a TAD varies from 100kb to several megabases.

## Why are TADs important?

DNAs were long believed to be mingled and intertwined in the nucleus like a bowl of spaghetti. However, the Hi-C contact frequency maps revealed more organized chromatin structures on different scales, including TADs. 

The majority of observed interactions between promoters and enhancers do not cross TAD boundaries [2]. Removing a TAD boundary can form new promoter-enhancer contacts. It has been proposed that TADs constitute functional units in the genome, important for the correct regulation of gene expression. TADs co-localize regulatory elements with their target genes, and are thought to promote co-regulation of the genes they contain, creating “gene regulatory domains” [3]. Disrupted TAD boundaries are associated with diseases, such as cancer.

Divergent CTCF sites were found to be enriched at TAD boundaries. One of the proposed mechanisms for the formation of TADS was loop extrusion. In this mechanism, cohesins extrude DNA loops until encounter divergent CTCF sites [4]. DNA sequences on the loop self interact more than interacting with sequences out of the loop. 

![alt text](https://ars.els-cdn.com/content/image/1-s2.0-S0955067420300570-gr1.jpg)

Recent studies in single-cell Hi-C and high-resolution microscopy data revealed that TAD-like structures were also present on the single-cell level. However, the TAD-like structures are highly variable from cell to cell, with a non-zero boundary probability across the genome [5]. Moreover, single-cell level TAD-like structures were observed in cohesion-depleted cells whereas ensemble-averaged TAD structures disappeared in bulk Hi-C data [6]. This indicated that loop extrusion is not sufficient to explain TAD formations. Other mechanisms such as thermodynamic models of phase separations were proposed. 

![alt text](https://ars.els-cdn.com/content/image/1-s2.0-S0955067420300570-gr1.jpg)

In summary, understanding the formation and effects of TAD structures will help us understand chromatin dynamics and gene regulations, and potentially provide insights into treatments of diseases.
