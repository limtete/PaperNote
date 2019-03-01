## Links
[Dual Graph Convolutional Networks for Graph-Based Semi-Supervised Classification](http://delivery.acm.org/10.1145/3190000/3186116/p499-zhuang.pdf?ip=103.88.46.210&id=3186116&acc=OPEN&key=4D4702B0C3E38B35%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35%2E6D218144511F3437&__acm__=1551360333_793e487a4141e6870da8efdfb090b65b)

## [Round1] Big Que(What the whole field are concerned about)
Use DL method to mine structure data

## [Round1] Background(< 5 sentences)
**keywords**: Duality
1. GNNs/GGsNNs/SpectralCNNs+/ChebNet/GCN/PATCHY-SAN/DCN
    > NNs to embed in graph space
    > Spatial && Spectral
    > Extract both local and global assumption, which PATCHY-SAN fails
1. Graph embedding vs. graph laplacian
    > combine them together by PPMI matrix
    > Implicit vs. explicit
1. graph-based semi-supervised learning

## [Round1] Specific Que
embed additional info offered by edge/global structure into local assumption
in graph-based semi-supervised node classification

## [Round1] Scheme
1. combine supervised and unsupervised loss together
1. combine local assumption and global assumption

## [Round1] Methodology
1. local assumption
1. global assumption
    1. frequency matrix
    1. PPMI matrix
1. unsupervised temporal loss
    1. supervised/local-assumption loss: CE
    1. unsupervised/global-assumption loss: MSD
1. architecture

## [Round1] Result
1. Task: semi-supervised graph node classification
1. Dataset: Citesee/Cora/Pubmed/NELL/Simplified NELL
1. Baseline: GCN/PLANETOID/DeepWalk
1. Result:
    1. [Sub1] Performance: acc
        > STOA
    1. [Sub2] Intepretation: regularization weight
    1. [Sub3] Interpretation: shifted PPMI matrix

## [Round2] Introspect (before reading the interpretation section)

## [Round2] Other Review [Survey/Twitter/OpenReview/]

## [Round1] Summary
1. This paper is well written, especially the introduction/background parts, which give a
really good starting point for summarizing related methods these days
    1. global assumption && local assumption
    1. spatial domain && spectral domain
    1. explicit learning && implicit learning
1. This work deals with what left behind by DCNs. In DCNs paper, the latter part of experiment,
the authors point out that while DCNs succeed in find local info, it fails to extract global structure
info. In DGCN, they offer a way to deal with global info, by "**duality**"

## [Round1&2] Ref (Further reading && Comparing with this work)
1. Deep Learning on Graphs: A Survey. Ziwei Zhang, Peng Cui, Wenwu Zhu. 2018
1. [reviews](https://media.nips.cc/nipsbooks/nipspapers/paper_files/nips29/reviews/1073.html)
