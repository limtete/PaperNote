## Links
[Learning Convolutional Neural Networks for Graphs](http://proceedings.mlr.press/v48/niepert16.pdf)

## Big Que(What the whole field are concerned about?)
Bring CNNs to bear on a large class of graph-based learning problems.

## Background(< 5 sentences)
one word:
1. graph kernels:
    1. skew spectrum kernel
    1. graphlet-based kernel
        1. Weisfeiler-Lehman kernel
        1. deep graph kernel/graph invariant kernel
    > limited, fixed and hand-crafted kernels, not data-driven learnt
1. GNNs/GGsNNs/SpectralCNNs/ChebNet/Neural FPs:

## Specific Que
1. Graph classification/regression
1. graph representation learning + downstream task

## Scheme
1. Select a fixed-length sequence of nodes from the graph
    > arbitrary number of nodes --> fixed number of nodes
1. Assemble a fixed-size neighborhood for each node in the selected sequence
    > ordering
1. Normalize the extracted neighborhood graph
    > graph representation --> vector space representation
1. learn neighborhood representations with CNNs from the resulting sequence of patches.
    > embed the graph in an Euclidean space

## Methodology
### framework
1. preprocess:
    1. **select**: graph labeling
    1. **assemble**: form a neighbor to normalize
    1. **normalize**: form receptive field
        > Weisfeiler-Lehman: one possible labeling procedure to compute receptive fields
1. normal CNNs
1. downstream-specific method

## Result
1. Runtime Analysis
1. Feature Visualization
1. Graph Classification
    * Objective: assign graphs to one of several categories
    * Dataset:
        1. standard benchmark datasets: MUTAG/PCT/NCI1/NCI109/PROTEIN/D&D
        1. social graph datasets: COLLAB/IMDB-B/IMDB-M/RE-B/RE-M5k/RE-M10k
    * Result:
        1. SOTA on standard benchmark datasets and outperforms on social graph
        1. But the ACC of all methods are still low

## Introspect (before reading the interpretation section)

## Other Review [Survey/Twitter/OpenReview/]

## Summary
PATCHY-SAN embeds the graph into Euclidean Space then use the normal CNNs to get graph
embedding. It offers a new preprocessing workflow of "select-assemble-normalize" to process
arbitrary input size. Then ensembled with normal CNN, it can extract meanful embedding for
graph. Node attributes and edge attributes, directed or not can all be dealed. What remains
thinking is:
1. Defferrard in his slide(Ref.1) demonstrates that extrinsic method suffers from the high-dim
1. Can the preprocess be learnt by data? Or to say, End-to-end way. Clearly, this pipeline most
effects the performance.
1. PATCHY-SAN defines a spatial-domain conv operation, but this operator is not learnt like CNNs
in Euclidean Space. Data drives a labeling algo, as above demonstrates, not end-to-end way.

## Ref (Further reading && Comparing with this work)
1.[Defferrard's slide for ChebNets in ICLR2017](https://ndownloader.figshare.com/files/7253636)
    > Extrinsic: embed the graph in an Euclidean space. (Possibly very high-dimensional)
1. Deep Learning on Graphs: A Survey. Ziwei Zhang, Peng Cui, Wenwu Zhu. 2018
