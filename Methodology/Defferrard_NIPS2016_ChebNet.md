## Links
[Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering](https://github.com/naganandy/graph-based-deep-learning-literature/blob/master/conference-publications/folders/chebnet_nips16/README.md)

## Big Que(What the whole field are concerned about?)
1. Extract stationality(invariance) and composation(locality) in graph data
1. locality, stationality and composation are keys of CNNs in Euclidean space
    * Localization: compact filters for low complexity
    * Stationarity: translation invariance
    * Compositionality: analysis with a filterbank
1. Using the structure: bridging graphs && NNs
    * Extrinsic: embed the graph in an Euclidean space.[No recommend: Possibly very high-dimensional]
    * Intrinsic: a Neural Net working on graph-structured data.

## Background(< 5 sentences)
keyword:
1. GSP defines: standard operation, multiscale pyramid transform, uncertainty principle
2. GNNs/GGsNNs offers framework for ChebNet
3. local receptive field offers basic ideas: composation, similarity measure, connecting choice
4. SpectralCNNs use stationarity property as weight-sharing strategy
    > this requires ordering neighbors which could be missing in some real problem
    > spatial domain:  needs to match local neighbors but no unique defination of tranlation
    > spectral domain: localization is well-defined but not naturally got, translation is costly

## Specific Que
Define localized graph filters which are efficient to evaluate and learn
1. localized
1. efficient

## Scheme
1. Design localized conv filters on graphs
1. graph coarsening
    > group together similar vertices
1. graph pooling
    > trade spatial resolution for higher filter resolution

## Methodology
1. filters: def --> polynomial parametrization --> recursive form --> learnable
    1. spectral filter defined by GSP
    1. polynomial parametrization
    1. recursive form for fast filtering: Chebyshev expansion; Lanczos algorithm(future work)
    1. learnable
1. graph coarsening
    1. two basic considering:
        1. why use coarsening: neighborhood = multi-scale clustering by similarity;
        1. ref[28] and Kron reduction: future work
        1. Graclus multilevel clustering algo
1. graph pooling: arrange[? don't understand]
    1. create a balanced binary tree
    1. rearrange the vertices

## Result
1. Image Classification:
    * Objective:
        1. snaity check
        1. sample graph verification
    * Data: Mnist with weight construction(Gaussian)
1. Text Categorization
    * Objective: versatility; feature graph verification
    * Data: 20NEWS
1. Computation efficiency
    * Objective:
        * efficiency: training time && speedups
        * outperformance
    * Data: MNIST/20NEWS
1. Influence of Graph Construction Quality
    * Objective: ways of construction can influence performance
    * Data: 20NEWS/LSHForest

## Introspect (before reading the interpretation section)
1. fast but what about efficient?
1. Comparation with SpectralCNNs?
1. Real application: graph construction is varified; but what the real graph in life?
    1. Knowledge graph
    1. social network
1. Graph construction:
    1. MNIST: using only coordinations(edges), how to integrate the node(pixel) value?

## Other Review [Survey/Twitter/OpenReview/]
[NIPS OpenReview](http://media.nips.cc/nipsbooks/nipspapers/paper_files/nips29/reviews/1911.html).
1. promising
1. hard to understand
1. not clear:
    1. the presentation of the ideas and the theory rather poor.
    1. The experiments is not obvious that the results are definite.

## Summary
Based on the work of SpectralCNNs, this paper present the idea of localization and computation efficiency,
both are defined in spectral domain by graph signal processing and Chebyshiv expansion. Experiments demonstrate
that computation is efficient, and graph construction is a bottleneck to system performance. Further work considers
two directions: first, using more advanced GSP tech to enhance defination, conv and coarsening may use different
ideas; second, this paper primarily conducts its idea on artificially dataset, efforts should be made to use the
framework on real problem like knowledge graph. From my opinion, ideas listed below may be further considered:
1. Use both node attributes and edge attributes?
1. Graph type should be more rebust? (heterogeneous, directed, dynamic)
1. Real application

## Ref
1. Deep Learning on Graphs: A Survey. Ziwei Zhang, Peng Cui, Wenwu Zhu. 2018
1. slides: https://ndownloader.figshare.com/files/7253636
