## [Diffusion-Convolutional Neural Networks](https://papers.nips.cc/paper/6212-diffusion-convolutional-neural-networks)

## [Round1] Big Que(What the whole field are concerned about)
Combination of DL method and structured data

## [Round1] Background(< 5 sentences)
**keywords**: diffusion other than ordering
1. Two direction:
    1. graph embedding methods(a Neural Net working on graph-structured data)
        > DeepWalk, GCNs, etc.
    1. graph laplacian methods(embed the graph in an Euclidean space)
        > embed to a Euclidean space and use normalized FNNs/CNNs/...
        > prior assumption is weak: connected node --> same label
1. GNNs/SpectralCNN+/ChebNet/NeuralFPs
    > faster and also less preprocessing
1. Probabilistic Relational Models
    > optimization is faster than CRFs
1. Kernel Methods: similarity measures
    > weights are learnt
    > use both node feature and graph structure
    > representation has lower-dim

## [Round1] Specific Que
**Main Que**:
> Can representation by graph diffusion perform better than graph itself in downstream tasks?
    1. higher accuracy?
    1. more flexible: use as much infomation as possible with as little preprocess as possible
    1. faster: both training and testing

## [Round1] Scheme
1. Math Concept: for formalization
1. Core idea: diffusion
    > offers an mechanism of ordering/structure in graph space
1. Task: for justification
    1. learning to predict label ---> classification
    1. semi-supervised setting: One-shot

## [Round1] Methodology
1. diffusion + convolution
    1. diffusion:  measure of the level of connectivity between any two nodes
    in a graph given all paths
    1. convolution
        1. feature learning
        1. parameter tying
        1. invariance
    1. operation: **"grid-like neighbor" in diffusion-defined meaning**
        > a mapping from nodes and their features to the results of
        a diffusion process that begins at that node
1. no pooling, node attributes can be added

## [Round1] Result
1. Node classification
    * Dataset: Cora/Pubmed
    * Baseline:
        1. L1-regularized logistic regression: l1logistic
        1. L2-regularized logistic regression: l2logistic
        1. exponential diffusion diffusion kernels-on-graphs: KED
        1. Laplacian exponential diffusion kernels-on-graphs: KLED
        1. partially-observed conditional random field with loopy belief propagation: CRF-LBP
    * Result: SOTA
1. Graph Classification
    * Dataset: NCI1/NCI109/MUTAG/PCI/ENZYMES
    * Baseline:
        1. l1logistic
        1. l2logistic
        1. Weisfeiler-Lehman subtree deep graph kernel: deepWL
    * Results: no clear best model choice
        > while diffusion processes are an effective representation for nodes, they do
        a poor job of summarizing entire graphs.

## [Round2] Introspect (before reading the interpretation section)

## [Round2] Other Review [Survey/Twitter/OpenReview/]

## [Round1] Summary
1. Compared to PATCHY-SAN by Niepert(ICML2016), DCNs offer a learning procedure to select-assemble-normalize
in the meaning of diffusion mechanism. This **learning(data-driven)** way is what i think most interesting.
This **diffusion mechanism** lay a light upon consideration about other physic-based mechinism, force, heat
or electronic, etc. Diffusion is a width-first way.
1. Performance on graph classification is poor. Local structure are well extracted while the global structure
cannot be got well.

## [Round1&2] Ref (Further reading && Comparing with this work)
1. Deep Learning on Graphs: A Survey. Ziwei Zhang, Peng Cui, Wenwu Zhu. 2018
1. [reviews](https://media.nips.cc/nipsbooks/nipspapers/paper_files/nips29/reviews/1073.html)
