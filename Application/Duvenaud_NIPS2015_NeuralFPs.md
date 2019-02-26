## Links
[Convolutional Networks on Graphs for Learning Molecular Fingerprints](https://arxiv.org/abs/1509.09292)

## Big Que(What the whole field are concerned about?)
**Materials design: Predict properties of novel molecules by generalizing from examples**

## Background(< 5 sentences)
keyword: arbitrary size, graph-driven input
1. NNs for QSAR
1. neural graph FPs: [15]
    > not scalable due to its distinct graphs created
1. CNNs: [12]
    > fixed computational graph, not fit for varying-length application like molecules
1. NNs on fixed graph: SpectralCNNs
    > fixed graph structure
1. NNs on input-dependent graphs: GNNs[16][9]
    > offers basic idea, and replaced by modern SGD to the QSAR pipeline
1. Unrolled inference algorithm: [9]
    > theoretical foundation: connection between iterative inference procedure and RNNs

## Specific Que
Use data-driven features instead of hand-crafted features.

## Scheme
 design a differentiable generalization of circular fingerprints

## Methodology
1. differentiate hash function as a single layer of NNs
1. differentiate indexing as softmax func
1. canonicalized concatenation as sum: permutation-invariance

## Result
1. Neural FPs feats similar to circular FPs
1. predictive performance are better: feats --> linear regression

## Introspect(what it is && does it answer the specific que)
1. Distance/Correlation Exp: show the similarity between Neural FPs feature and Circular FPs feature
    > similarity
1. Predict performance by feats + linear regression on 3 dataset: outperform the state-of-the-art
    > performance
My introspection:
1. Why similar but perform better? So what does this similarity mean?

## Other Review[Survey/Twitter/OpenReview/]
1. [T.Kipf on OpenReview](https://openreview.net/forum?id=SJU4ayYgl):Duvenaud et al. 2015 consider classification of graphs with narrow node degree distributions (e.g. graphs with nodes that only have a maximum of 5 neighbors) and introduce a specialized architecture for this case where they assign node-degree specific weight matrices. For graphs with very wide node degree distributions (such as citation networks) this becomes impractical.

## Summary
2 major contribution:
1. flexibility: varing-length input
    > By permutation-invariant sum and NN propagation
1. data-driven feature instead of hand-crafted feature

## Ref
1. Deep Learning on Graphs: A Survey. Ziwei Zhang, Peng Cui, Wenwu Zhu. 2018
1. [Reviews](https://media.nips.cc/nipsbooks/nipspapers/paper_files/nips28/reviews/1321.html)
