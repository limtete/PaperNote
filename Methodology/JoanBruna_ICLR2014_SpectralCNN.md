## Links
[Spectral Networks and Locally Connected Networks on Graphs](https://github.com/naganandy/graph-based-deep-learning-literature/blob/master/conference-publications/folders/graphcnn_iclr14/README.md) (ICLR 2014)
## Big Que(What the whole field are concerned about?)
1. Exploiting the grid structure of different types of data(image, audio, etc) with CNNs has been essential to the recent breakthrough results in various pattern recognition tasks.
1. This paper explores generalizing CNNs from grids to weighted graphs.

## Background(< 5 sentences)
one word: Adjust
1. 2 lines of related work: graph wavelet; discovering grid structure from data
1. graph wavelet: hand engineering, not learning and generalize well to other poststeps
1. discovering grid structure from data: side support/evdience that this could work; like Fourier synthesis theorem
1. multigrid clustering method: provides interpretation for subsampling.

## Specific Que
constructions of meanful conv_operator on graphs other than regular grids.

## Scheme
1. local connectivity/hierarchical composition --> Spatial
1. harmonic analysis on graph --> graph Laplace --> Spectral

## Methodology
1. Spatial:
    1. define locality with neighborhood concept
    1. define multigrid clustering method
    1. put 1] and 2] together to define conv layer
    1. define update procedure of weight matrix, which is used by each layer's input x

1. Spectral:
    1. assumption: use combinatorial Laplacian
    1. define the conv layer based on smoothness/graph Laplacian
    1. computation complexity reduction: choosing leaning filter to be diagnoal

## Result
    1. Self-made Dataset: subsampling MNIST
        * Fig3: sampled images
        * Fig4: agglomerative cluster algo result
        * Fig5: eigenvectors of unnormalized graph Laplacian
        * Fig6: learnt filters
        * Table1:
            * baseline: nearest neighbors, fully connected NN
            * input_dim: 400
            * spatial: 1 hidden layer; 2 hidden layer
            * spectral: 3 different size cubic spline kernel
    1. Self-made Dataset: project to sphere manifold
        * Table2:
        * Fig7: data example
        * Fig8: eigenvector heat map
        * Fig9: learnt filter

## Introspect (before reading the interpretation section)
    1. real-world data:
        this paper uses a man-made dataset to simulate, more work should be done on real que and real data.
        Application is more needed.
        > This is what "Deep Convolutional Networks on Graph-Structured Data" does!!!
    1. deeper layer
    1. direct, heterogeneous, dynamic graph
        1. direct: what does the adjancy matrix look like?
        1. heterogeneous: node or edge. This paper doesn't use node attributes, only link weight
        1. dynamic: no idea about this
    1. computation is really high for eigenvector
    1. Experiment is enough to support.

## Other Review [Survey/Twitter/OpenReview/]
1. [Deep Learning on Graphs: A Survey, Wenwu Zhu]:
    * Pros: first spectral method to adjust CNNs into graph domain
    * Cons:
        1. High computation due to full stack of eigenvector
        1. domain specific, no easy wat to transfer learnt basis
1. OpenReview
    * Anonymous1:
        * Pros:
            1. Great extension of CNNs
            1. Results based on profound understanding of harmonic analysis, not trial and error
        * Cons:
            1. Extremely difficult to read without background of harmonic analysis
            1. Experiment a bit weak.
1. David Duvenaud [NeuralFPs]:
    > the graph structure is fixed, and each training example differs only in having different features
    at the vertices of the same graph

## Ref
1. The Emerging Field of Signal Processing on Graphs: graph DSP的基本概念，定义
1. Deep Learning on Graphs: A Survey. Ziwei Zhang, Peng Cui, Wenwu Zhu. 2018
