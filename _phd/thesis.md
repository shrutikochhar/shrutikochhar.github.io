---
title: "Unification of Genomic Representations"
collection: phd
type: "Proposal"
about: "Thesis"
permalink: /phd/thesis
date: 2020-10-05
---

In my Ph.D. research, we build informative genomic representations from epigenomic, functional, and structural genomic data, which will be position-specific and maybe celltype-specific or pan-celltype. These representations will be helpful for various tasks, including predicting known genomic phenomena, locating genomic elements that drive three-dimensional (3D) conformation, and inferring 3D chromatin structure. In the process of building these representations, we aim to study two broad classes of models that differ in the underlying structure they use to represent the genome, namely, sequential and graphical models which use deep neural networks. Borrowing techniques from deep learning that work on sequences and graphs, we analyze their suitability for different genomic datasets and tasks. The genome is heavily correlated with nearby positions, and folds in 3D space interacting with far-away positions. These two genomic properties render deep sequential and graphical models a natural choice to handle both epigenomic and structural genomic data. 

## Epi-LSTM
<p align="center">
<img align="center" src="https://github.com/kevinbdsouza/kevinbdsouza.github.io/blob/master/files/epi-lstm.png?raw=true">
</p>

In the first part of my research, we employ sequential models to form representations of the epigenome and chromatin structure. The availability of thousands of epigenomic assays necessitates compressed representations that summarize the epigenetic landscape of the genome. Many methods have been proposed to form epigenomic representations [1, 2, 3, 4, 5]. Most existing methods produce celltype-specific representations which correspond poorly to conceptualizations of genomic elements. Joint methods aim to improve epigenomic representations by simultaneously using many cell types and sharing position-specific information between them [6, 7, 8, 9]. These methods are accurate but produce different representations for each cell type. On the other hand, stacked methods take data from all available cell types to produce pan-celltype representations, discrete [10, 11] or continuous [12, 13]. Avocado [12] uses separate embeddings for each genomic position, assay type, and cell type and couples this with a feed-forward network that infers unperformed assays. Towards forming pan-celltype epigenomic representations, we propose to improve upon existing feed-forward neural architectures [12] by using a deep long short-term memory (LSTM) [14] recurrent neural network autoencoder called Epi-LSTM [15] to capture the neighborhood dependencies in the epigenomic data. The latent representations from this model capture a variety of genomic phenomena, including frequently interacting regions, promoter-enhancer interactions, gene expression, evolutionary conservation, and replication timing. Moreover, the sequential nature of our model yields smoother epigenomic representations along the genomic axis.

## Hi-C-LSTM
<p align="center">
<img align="center" src="https://github.com/kevinbdsouza/kevinbdsouza.github.io/blob/master/files/hi-c-lstm.png?raw=true">
</p>

While epigenomic assays detail the interaction of proteins with the genome, experiments like Hi-C [16, 17] identify genome-wide long-range interactions and enhance our understanding of genome organization by allowing us to analyze the resulting contact matrix using deep learning methods. MATCHA [18] uses hypergraph representation learning to locate multi-way interactions, while Akita [19] uses a convolutional neural network that predicts chromatin contacts from the nucleotide sequence alone and can be used to perform in-silico mutagenesis. Both these methods do not form pairwise Hi-C representations. SNIPER [20] uses a feed-forward network, and SCI [21] uses graph embedding to form Hi-C representations; however, they do not account for the sequential nature of the genome. SNIPER takes the inter-chromosomal contacts as input which, while helpful in locating domain-level structures, might not be the best suited for element-level usage. Moreover, both methods have not demonstrated the capability of performing in-silico mutagenesis. Towards forming position-specific intra-chromosomal representations, we propose to use a deep LSTM model called Hi-C-LSTM [22] that predicts the intra-chromosomal contacts from the pairwise node information.

<p align="center">
<img align="center" src="https://github.com/kevinbdsouza/kevinbdsouza.github.io/blob/master/files/map_tasks.png?raw=true">
</p>

The representations from our model capture a variety of genomic phenomena and distinguish genomic regions known to cluster in 3D space. Feature importance analysis also reveals association with genomic elements driving 3D conformation and transcription factors such as CCCTC-binding factor (CTCF) and cohesin subunits known to mediate chromatin conformation [23, 24, 25, 26]. A sequential contact generation model is a promising candidate to understand 3D chromatin conformation in light of the results obtained.

<p align="center">
<img align="center" src="https://github.com/kevinbdsouza/kevinbdsouza.github.io/blob/master/files/melo_fusion.png?raw=true">
</p>


To demonstrate that our chromatin conformation model is effective at contact generation, we perform in-silico duplication of a 2.1 Mbp region in chromosome 7 as seen in Cooks syndrome [29] and saw that the predicted Hi-C map shows the presence of a new chromatin domain (neo-TAD). These experiments validate the capability of our model to perform in-silico mutagenesis experiments.

## Building Blocks
<p align="center">
<img align="center" src="https://github.com/kevinbdsouza/kevinbdsouza.github.io/blob/master/files/blocks.png?raw=true">
</p>

## Structure 
<p align="center">
<img align="center" src="https://github.com/kevinbdsouza/kevinbdsouza.github.io/blob/master/files/structure.png?raw=true">
</p>

Both the epigenomic model and the chromatin conformation model use an underlying sequential structure to model that genome; however, they differ in the task they are trying to accomplish. While our epigenomic sequential model reconstructs the epigenomic data given to it as input [15], our chromatin conformation model seeks to predict the pairwise contact data between nodes by using just the nodes’ positional information [22]. As expected, we observe that prediction is much more challenging than reconstruction because of the model’s lack of complete knowledge about the nature of continuous predictions it is trying to make. In the second part of my research, we aim to study these two tasks further and the crucial differences in their approach to creating genomic representations. Along with these tasks, we also include a third classification task, which involves forming representations by trying to classify genomic regions. These three tasks are fundamentally different, and studying the similarities and differences between the representations they form can provide us insights into the nature of epigenomic and chromatin conformation data.

## Node Classification 
<p align="center">
<img align="center" src="https://github.com/kevinbdsouza/kevinbdsouza.github.io/blob/master/files/graph_class.png?raw=true">
</p>


In the third and final part, we will employ graphical models to form representations of the epigenome and chromatin structure. Methods that use graphs to create genomic representations exist. While ChromeGCN [45] uses a graph convolutional network (GCN) for epigenetic state prediction by fusing nucleotide sequence and 3D structure information, a similar GCN model also predicts gene expression [46]; however, SCI [21] and MATCHA [18] are the only methods that form representations (Hi-C) and do so using graph embedding and hypergraph representation learning respectively. We will explore a generalization of transformers for graphs [47]. Transformers were originally designed to operate on fully connected graphs [48], which leads to poor performance when the graph topology is essential. The graph-transformer model takes into account the neighborhood connectivity and includes positional representations for each node. Moreover, the model also forms edge representations. We will mainly use this model for classification and reconstruction tasks and compare the representations obtained from our sequential models.

## Hi-C Graph Generation
<p align="center">
<img align="center" src="https://github.com/kevinbdsouza/kevinbdsouza.github.io/blob/master/files/graph_hic_generation.png?raw=true">
</p>


Our three-part research aims to unify the two main structures of sequences and graphs used to form genomic representations and the main inference, reconstruction, and classification tasks used to obtain these representations. We demonstrate that while these representations’ utility depends on the structure used and the task trained on, they are helpful for non-trivial downstream tasks like pan-celltype classification of genomic phenomena, in-silico mutagenesis, and inference of 3D chromatin structure.


### References 
1. M. Hoffman, O. J. Buske, J. Wang, Z. Weng, J. A. Bilmes, & W. S. Noble. Unsupervised pattern discovery in human chromatin structure through genomic segmentation. Nature methods, 9(5), 473-476. 2012. 
2. J. Ernst, & M. Kellis. ChromHMM: automating chromatin-state discovery and characterization. Nature methods, 9(3), 215. 2012. 
3. N. Day, A. Hemmaplardh, R. E. Thurman, J. A. Stamatoyannopoulos, & W. S. Noble. Unsupervised segmentation of continuous genomic data. Bioinformatics, 23(11), 1424-1426. 2007. 
4. A. Mammana, & HR. Chung. Chromatin segmentation based on a probabilistic model for read counts explains a large portion of the epigenome. Genome Biology 16(1), 151. 2015. 
5. S. G. Coetzee, Z. Ramjan, H. Q. Dinh, B. P. Berman, & D. J. Hazelett. Statehub-statepaintr: rapid and reproducible chromatin state evaluation for custom genome annotation. BioRxiv, 127720. 2017.
6. B. Chen, N. S. Kenari, & M. W. Libbrecht. Continuous chromatin state feature annotation of the human epigenome. bioRxiv, 473017. 2018.
7. Y. Zhang, L. An, F. Yue, & R. C. Hardison. Jointly characterizing epigenetic dynamics across multiple human cell types. Nucleic acids research 44(14), 6721-6731. 2016. 
8. M. W. Libbrecht, M. M. Hoffman, J. A. Bilmes, & W. S. Noble. Entropic graph-based posterior regularization: Extended version. In Proceedings of the International Conference on Machine Learning. 2015. 
9. M. W. Libbrecht, F. Ay, M. M. Hoffman, D. M. Gilbert, J. A. Bilmes, & W. S. Noble. Joint annotation of chromatin state and chromatin conformation reveals relationships among domain types and identifies domains of cell-type-specific expression. Genome Research, 25(4), 544-557. 2015.
10. M. M. Hoffman, J. Ernst, S. P. Wilder, A. Kundaje, R. S. Harris, M. Libbrecht, et al. Integrative annotation of chromatin elements from ENCODE data. Nucleic acids research, 41(2), 827-841. 2013. 
11. M. W. Libbrecht, O. L. Rodriguez, Z. Weng, J. A. Bilmes, M. M. Hoffman, & W. S. Noble. A unified encyclopedia of human functional DNA elements through fully automated annotation of 164 human cell types. Genome Biology, 20(1), 180. 2019. 
12. J. Schreiber, T. Durham, J. Bilmes, & W. S. Noble. Multi-scale deep tensor factorization learns a latent representation of the human epigenome. BioRxiv, 364976. 2019.
13. T. J. Durham, M. W. Libbrecht, J. J. Howbert, J. Bilmes, & W. S. Noble. PREDICTD parallel epigenomics data imputation with cloudbased tensor decomposition. Nature communications, 9(1), 1402. 2018.
14. S. Hochreiter, & J. Schmidhuber. Long short-term memory. Neural computation, 9(8), 1735-1780. 1997.
15. K. B. Dsouza, A. Y. Li, V. Bhargava, & M. W. Libbrecht. Latent representation of the human pan-celltype epigenome through a deep recurrent neural network. IEEE/ACM Transactions on Computational Biology and Bioinformatics. 2021. 
16. N. L Van Berkum, E. Lieberman-Aiden, L. Williams, M. Imakaev, A. Gnirke, L. A. Mirny, et al. Hi-C: a method to study the three-dimensional architecture of genomes. JoVE (Journal of Visualized Experiments). 39:e1869. 2010.
17. S. S. Rao, M. H. Huntley, N. C. Durand, E. K. Stamenova, I. D. Bochkov, J. T. Robinson, et al. A 3D map of the human genome at kilobase resolution reveals principles of chromatin looping. Cell. 159:1665-80. 2014.
18. R. Zhang, & J. Ma. Probing multi-way chromatin interaction with hypergraph representation learning. Cell Systems. 10:397-407. 2020.
19. G. Fudenberg, D. R. Kelley, & K. S. Pollard. Predicting 3D genome folding from DNA sequence with Akita. Nature Methods. 17:1111-1117. 2020.
20. K. Xiong, & J. Ma. Revealing Hi-C subcompartments by imputing inter-chromosomal chromatin interactions. Nature communications. 10. 2019.
21. H. Ashoor, X. Chen, W. Rosikiewicz, J. Wang, A. Cheng, P. Wang, et al. Graph embedding and unsupervised learning predict genomic sub-compartments from HiC chromatin interaction data. Nature communications. 11:1. 2020.
22. K. B. Dsouza, A. Maslova, A. J. Ediem, M. Merkenschlager, V. K. Bhargava, & M. W. Libbrecht. Hi-C-LSTM: Learning representations of chromatin contacts using a recurrent neural network identifies genomic drivers of conformation. To be Submitted. Genome Biology. 
23. S. Cuddapah, R. Jothi, D. E. Schones, T. Y. Roh, K. Cui, & K. Zhao. Global analysis of the insulator binding protein CTCF in chromatin barrier regions reveals demarcation of active and repressive domains. Genome research. 19:24-32. 2009.
24. J. E. Phillips, & V. G. Corces. CTCF: master weaver of the genome. Cell. 137:1194-211. 2009.
25. E. Splinter, H. Heath, J. Kooren, R. J. Palstra, P. Klous, F. Grosveld, et al. CTCF mediates long-range chromatin looping and local histone modification in the $\beta$-globin locus. Genes & development. 20:2349-54. 2006.
26. A. L. Sanborn, S. S. Rao, S. C. Huang, N. C. Durand, M. H. Huntley, A. I. Jewett, et al. Chromatin extrusion explains key features of loop and domain formation in wild-type and engineered genomes. Proceedings of the National Academy of Sciences. 112:E6456-65. 2015.
27. E. P. Nora, A. Goloborodko, A. L. Valton, J. H. Gibcus, A. Uebersohn, N. Abdennur, et al. Targeted degradation of CTCF decouples local insulation of chromosome domains from genomic compartmentalization. Cell. 169(5): 930-944. 2017.
28. S. S. Rao, S. C. Huang, B. G. St Hilaire, J. M. Engreitz, E. M. Perez, K. R. Kieffer-Kwon, et al. Cohesin loss eliminates all loop domains. Cell. 171:305-20. 2017.
29. U. S. Melo, R. Schöpflin, R. Acuna-Hidalgo, M. A. Mensah, B. Fischer-Zirnsak, M. Holtgrewe, et al. Hi-C identifies complex genomic rearrangements and TAD-shuffling in developmental diseases. The American Journal of Human Genetics. 106(6):872-884. 2020.
30. Y. Guo, Q. Xu, D. Canzio, J. Shou, J. Li, D. U. Gorkin, et al. CRISPR inversion of CTCF sites alters genome topology and enhancer/promoter function. Cell. 162:900-10. 2015.
31. E. M. Darrow, M. H. Huntley, O. Dudchenko, E. K. Stamenova, N. C. Durand, Z. Sun, et al. Deletion of DXZ4 on the human inactive X chromosome alters higher-order genome architecture. Proceedings of the National Academy of Sciences. 113:E4504-12. 2016.
32. J. Huang, K. Li, W. Cai, X. Liu, Y. Zhang, S. H. Orkin, et al. Dissecting super-enhancer hierarchy based on chromatin interactions. Nature communications. 9:1-2. 2018.
33. M. Rousseau, J. Fraser, M. A. Ferraiuolo, J. Dostie, & M. Blanchette. Three-dimensional modeling of chromatin structure from interaction frequency data using Markov chain Monte Carlo sampling. BMC Bioinformatics. 12(1):414. 2011.
34. M. Hu, K. Deng, Z. Qin, J. Dixon, S. Selvaraj, J. Fang, et al. Bayesian Inference of Spatial Organizations of Chromosomes. PLoS Computational Biology. 9(1). 2013. 
35. N. Varoquaux, F. Ay, W. S. Noble, & J. P. Vert. A statistical approach for inferring the 3D structure of the genome. Bioinformatics. 30(12):i26–i33. 2014. 
36. O. Oluwadare, Y. Zhang, & J. Cheng. A maximum-likelihood algorithm for reconstructing 3D structures of human chromosomes from chromosomal contact data. BMC genomics. 19(1):161. 2018. 
37. A. Lesne, J. Riposo, P. Roger, A. Cournac, & J. Mozziconacci. 3D genome reconstruction from chromosomal contacts. Nature Methods. 11(11):1141–1143. 2014.
38. T. Trieu, & J. Cheng. Large-scale reconstruction of 3D structures of human chromosomes from chromosomal contact data. Nucleic acids research. 42(7):e52. 2014.
39. L. Rieber, & S. Mahony. MiniMDS: 3D structural inference from high-resolution Hi-C data. Bioinformatics, 33(14):i261–i266. 2017. 
40. J. B. Kruskal. Multidimensional scaling by optimizing goodness of fit to a nonmetric hypothesis. Psychometrika. 29(1):1–27. 1964. 
41. G. Zhu, W. Deng, H. Hu, R. Ma, S. Zhang, J. Yang, et al. Reconstructing spatial organizations of chromosomes through manifold learning. Nucleic Acids Research. 2. 2018. 
42. B. C. Cristescu, Z. Borsos, J. Lygeros, M. R. Martínez, & M. A. Rapsomaniki. Inference of the three-dimensional chromatin structure and its temporal behavior. arXiv preprint. arXiv:1811.09619. 2018.
43. M. Trussart, F. Serra, D. Baù, I. Junier, L. Serrano, & M. A. Marti-Renom. Assessing the limits of restraint-based 3D modeling of genomes and genomic domains. Nucleic Acids Research. 43(7):3465–3477. 2015. 
44. H. Tanizawa, K.D. Kim, O. Iwasaki, & K.I. Noma. Architectural alterations of the fission yeast genome during the cell cycle. Nature Structural & Molecular Biology. 24(11):965–976. 2017. 
45. J. Lanchantin, & Y. Qi. Graph convolutional networks for epigenetic state prediction using both sequence and 3D genome data. Bioinformatics. 36:i659-i667. 2020.
46. J. Bigness, X. Loinaz, S. Patel, E. Larschan, & R. Singh. Integrating long-range regulatory interactions to predict gene expression using graph convolutional networks. bioRxiv. 2020-11. 2021.
47. V. P. Dwivedi, & X. Bresson. A generalization of transformer networks to graphs. arXiv preprint. arXiv:2012.09699. 2020.
48. A. Vaswani, N. Shazeer, N. Parmar, J. Uszkoreit, L. Jones, A. N. Gomez, et al. Attention is all you need. In Advances in neural information processing systems. 5998–6008. 2017.


