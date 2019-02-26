## Links
[Deep Convolutional Networks on Graph-Structured Data](https://arxiv.org/pdf/1506.05163)

## Big Que(What the whole field are concerned about?)
1. Using CNNs to extract grid-like locality of stationality, compositation is "silver bullet" in image/audio.
1. Exploiting underlying grid-like structure of graph data using CNNs

## Background(< 5 sentences)
keyword: general real data extention.
1. arch with local receptive field + similarity measurement for image recognition task.
    > no weight-sharing strategy
1. Graph Laplacian from SpectralCNNs
    > prior knowledge of graph
    > simple, low-dim graph
1. Shapenet:
    > prior knowledge of the specific manifolds

## Specific Que
1. Using SpectralCNNs in **high-dim** real data
1. Performance/**Parameters** comparison with FNNs.

## Scheme
1. Graph construction/estimation: build adjancy matrix from unstructured data by similarity measurement
    > from numeric feature to adjancy matrix measuring similarity
1. Model: SpectralCNN

## Methodology
1. Construction/Estimation
    1. Unsupervised way: Gaussian diffusion Kernel
        * Euclidean dist
        * Z-score
        * Square-correlation
        * mutual information
    1. Supervised way: Distill
        1. FNNs
        1. Use the 1st hidden layer's weight matrix as similarity measurement
1. Model/Pipline
    1. build graph: W, D
    1. compute eigenvector matrix U
    1. initialization filter kernel weight w
    1. forward/backward prop + hierarchical clustering

## Result
### Env
* torch
* custom CUDA backend
### Tasks
1. text categorization
    * dataset: Reuters
1. computational biology
    * dataset: Merck DPP4
1. computer vision
    * dataset: ImageNet

## Introspect (before reading the interpretation section)
1. Graph construction can be End-to-end way
1. Measurement(MSE) ploted in computation biology has any real meaning?
1. Can it compare with the-state-of-the-art method like ResNet?

## Other Review [Survey/Twitter/OpenReview/]
* **Deep Learning on Graphs: A Survey. Ziwei Zhang, Peng Cui, Wenwu Zhu. 2018**
1. Eigenvector computing leads to high computation, which means that large scale graph is impossible.
1. Eigenvector also means: domain specific, which limits generalization.

## Summary
This work is based on SpectralCNNs[Joan Bruna, 2013, ICLR], focusing spectral-domain method
to answer 2 questions:
1. Can SpectralCNNs be used in real unstructured data? (Does graph construction work?)
1. Is this pipeline, estimation and graph laplacian, meaningful? (Compared with FNNs baseline)

Experiments prove the disigning idea, leaving several points:
1. FFT-like approximation of eigenvector is badlly needed
1. locality may not exists in underlying data, thus soft panlelty is needed.

## Ref
1. Spectral networks and locally connected networks on graphs. ICLR 2014. J Bruna.
1. Deep Learning on Graphs: A Survey. Ziwei Zhang, Peng Cui, Wenwu Zhu. 2018

