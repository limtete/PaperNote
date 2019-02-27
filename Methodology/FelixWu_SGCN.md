## Links
[Simplifying Graph Convolutional Networks](https://arxiv.org/pdf/1902.07153v1.pdf)

## Big Que(What the whole field are concerned about?)
Extend CNNs-like method to graph-like data efficient and well-performed

## Background(< 5 sentences)
one word: simplicity
1. GCN-based methods perform well on graph application:
    * citation networks/social networks/applied chemistry/NLP/CV
    * SpectralCNNs/ChebNet/GCN/GAN/GraphSAGE/FastGCN/DCNN, etc
1. development curve of ML: initial, well-interpretable simplicity to need-driven but obfuscating complexity.
    > In GCNs case, a simpler predecessor is omissed
1. graph methodologies: offer bases
    1. graph embedding method
        > representing nodes as feature vectors in a high-dimensional continuous space
    1. graph laplacian method
        > introduce an additional regularization term based on graph structure which forces
        nodes to have similar labels to their neighbors and helps the models generalize

## Specific Que
Further simplify GCNs complexity for less demanding applications
    > Which means faster but rivals

## Scheme
1. repeatedly removing the nonlinearities between GCN layers
1. collapsing the resulting function into a single linear transformation
1. theoretical analysis from the graph convolution perspective

## Methodology
1. Ignore the Nonlinear function in propagation

## Result
1. Citation Networks & Social Networks
    * Dataset: Cora/Citeseer/Pubmed/Reddit
    * Type:
        1. semi-supervised node classification
        1. predict community structure
1. Downstream tasks
    1. Text classification
        * Object: assigns labels to documents
        * Dataset: 20NG(?20NEWS)/R8/R52/Ohsumed/MR
        * Result: reach new SOTA, better efficiency and similar performance with GCNs
    1. Semi-supervised user geolocation
        * Object: locates the “home” position of users on social media given users’ posts,
         connections among users, and a small number of labelled users.
        * Dataset: GEOTEXT/TWITTER-US/TWITTER-WORLD
        * Result: close to SOTA and better than GCNs(both performance and efficiency)
    1. Relation extraction
        * Object: predicting the relation between subject and object in a sentence
        * Dataset: TACRED
        * Result: make new SOTA
    1. Zero-shot image classification
        * Object: learning an image classifier without access to any images or labels from the test categories
        * Dataset: ImageNet
        * Result: far behind SOTA(ADGPM/EXEM 1-nns) but better than GCNs
    1. Graph classification
        * Object: use graph structure to categorize graphs
        * Data: NCI1/COLLAB/QM8
        * Result: far behind SOTA method(GIN/AdaLNet/LNet) but on par with GCN

## Introspect (before reading the interpretation section)
1. Under what circumstances is this simplification really needed? Suitable applying fields needs
to be present.
1. [Idea]Graph Transformer?
1. [Idea]Adjancy matrix: approximated by RNNs --> dynamic. Adjancy matrix in GCNs is static, so we can
use the local substructure of the graph, what if it can evolve and be approximated by RNNs

## Other Review [Survey/Twitter/OpenReview/]
Commitment about the idea "Remove nonlinear just the linear part" are dicussed on [Reddit](https://www.reddit.com/r/MachineLearning/comments/ati9q9/r_simplifying_graph_convolutional_networks_linear/)
## Summary
1. This paper concentrate on building simplicity in spectral domain for GNNs that can rival spatial-based
defination, withou loss of the elegent theoretical foundation from spectral-based defination.
1. The theoretical result that filters learnt actually serve as low-pass-type is wonderful.
1. It also matches SOTA for text classification on 20NEWS dataset.
1. Also it is well writen and can serve a supplimentary material for the original GCN paper by T.Kipf.
1. The "relation work" is what i prefer much, for it gives a high view about the graph methods
and summarize most recent work.

## Ref (Further reading)
1. [Reddit dicussion](https://www.reddit.com/r/MachineLearning/comments/ati9q9/r_simplifying_graph_convolutional_networks_linear/)
1. NGCN: Multi-scale graph convolution for semi-supervised node classification. Abu-El-Haija, S.
1. Rethinking knowledge graph propagation for zero-shot learning. Kampffmeyer, M.
    > GAN +KG
1. Attention models in graphs: A survey. Lee, J. B.
1. Lanczosnet: Multi-scale deep graph convolutional networks. ICLR’2019. Liao, R.
1. Thekumparampil, K. K. Attention-based graph neural network for semisupervised learning.
1. Velikovi, P. Deep Graph InfoMax. ICLR’2019
1. Wang, X. Zero-shot recognition via semantic embeddings and knowledge graphs. CVPR2018.
1. Xu, K. How powerful are graph neural networks? ICLR’2019
1. Yang, Z. Revisiting semi-supervised learning with graph embeddings. ICML’16
1. Yao, L. Graph convolutional networks
for text classification. AAAI’19
1. Zhang, J. Gaan: Gated attention networks for learning on large
and spatiotemporal graphs. UAI’2018
