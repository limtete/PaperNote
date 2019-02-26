## Links
[Semi-Supervised Classification with Graph Convolutional Networks](https://github.com/naganandy/graph-based-deep-learning-literature/blob/master/conference-publications/folders/gcn_iclr17/README.md)

## Big Que(What the whole field are concerned about?)
1. locality, stationality and composation are keys of CNNs in Euclidean space
    * Localization: compact filters for low complexity
    * Stationarity: translation invariance
    * Compositionality: analysis with a filterbank
1. Using the structure: bridging graphs && NNs
    * Extrinsic: embed the graph in an Euclidean space.[Not recommend: Possibly very high-dimensional]
    * Intrinsic: a Neural Net working on graph-structured data.

## Background(< 5 sentences)
keyword:
1. graph-based semi-supervised learning
    > assumption that connected nodes share same labels restricts model capacity
    1. graph Laplacian regularization
        1. label propagation
        1. manifold regularization
        1. deep semi-supervised embedding
    1. graph embedding-based approaches
        1. DeepWalk
        1. LINE
        1. node2vec
        1. Planetoid
            > multi-step pipeline is needed and optimized separately: randomwalk generation
1. neural networks on graphs
    1. GNNs --> GGsNNs --> NeuralFPs
        > degree-specific matrix restricts large scale application
    1. PATCHY-SAN/DCNN
        > Complexity
        > node-order defination
    1. SpectralCNNs/ChebNets
        > scalability
        > classification performance
1. [Weisfeiler-Lehman algorithm](http://deeploria.gforge.inria.fr/thomasTalk.pdf)

## Specific Que
node classification

## Scheme
1. fast approximate conv
1. application: semi-supervised node classification

## Methodology
1. Conv operation
    > spectral graph conv --> Chebyshev polynormial --> 1st order layer-wise linear model
1. Application:
    1. 2-layer
    1. CE criteria

## Result
1. Dataset
    * Citation networks
    * NELL: extracted from a KG
        1. concatenate node feature vector(5414 dim) with relation one-hot vector(55846 dim)
        to form feature vectors
    * Random graph: N nodes, 2N edges uniformly assigned
1. Setup
    * model: 2 layer (10 layer at Appendix B)
    * val set: 500 labeled samples; only for hyperparameter tuning, not training
    * test set: 1000 labeled samples
1. Exp
    1. Compare different models on multi-dataset
    1. Compare different version of GCNs on multi-dataset

## Introspect (interpretation of your own: what and why)
1. directed edge
1. two kinds of baslines are formulated in introduction:
    1. graph-based semi-supervised learning: regularization added
        > this is well compared
    1. SpectralCNNs/ChebNets/DCNNs, GNNs/GGsNNs/NeuralFPs
        > Not compared so-well as before
        >
## Other Review [Survey/Twitter/OpenReview/]
1. [OpenReview2](https://openreview.net/forum?id=SJU4ayYgl):
    1. there is no comparison with the family of iterative classifiers, which usually compare favorably, both in performance and training time, with regularization based approaches, although they are mostly used in inductive settings. Below are some references for this family of methods. (**DEALED BY THE AUTHOR**)
    1. The authors mention that more complex filters could be learned by stacking layers but they limit their architecture to one hidden layer. They should comment on the interest of using more layers for graph classification. (**DEALED BY THE AUTHOR**)
1. [inFERENCe](https://www.inference.vc/how-powerful-are-graph-convolutions-review-of-kipf-welling-2016-2/) and respondence from
[T.Kipf](https://tkipf.github.io/graph-convolutional-networks/#gcns-part-iii-embedding-the-karate-club-network)

## Summary
Use 1st order approximation rather than the full Chebyshev polynormials as filter coefficients, thus
give both scalibility and performance on real dataset a jump. Also different previous graph-based
semi-supervised learning, which appends another similarity regularization on lost function, this work
concatenates node features and edge features, and use CE criteria only.

## Ref
1. Deep Learning on Graphs: A Survey. Ziwei Zhang, Peng Cui, Wenwu Zhu. 2018
1. slides: https://ndownloader.figshare.com/files/7253636
1. [blog by inFERENCe](https://www.inference.vc/how-powerful-are-graph-convolutions-review-of-kipf-welling-2016-2/)
