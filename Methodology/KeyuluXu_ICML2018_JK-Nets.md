# [Representation Learning on Graphs with Jumping Knowledge Networks](http://proceedings.mlr.press/v80/xu18c/xu18c.pdf)

## [Round1] Big Que(What the whole field are concerned about)
Use DL method to graph

## [Round1] Background(< 5 sentences)
**keywords**: jump
1. representation learning of nodes has proved useful
1. neighborhood aggregation(message passing) scheme extends Weisfeiler-Lehman
1. residual connection + GCNs: deeper layer, but still worse performance
1. one fixed hop step doesn't always fit
1. subgraph structure influences

## [Round1] Specific Que
whether it is possible to adaptively adjust the influence radii for each node and task?

## [Round1] Scheme
1. mathematiclly prove substructure importance for aggregation
1. formalize layer-wise jump connection defination

## [Round1] Methodology
1. One component: intra-layer attention
   1. 3-method to aggregate: concatenation/max-pooling/LSTM-attention
1. Multi-baseline combined:

## [Round1] Result
1. Citeseer& Cora
    * Task: classify academic paper into different subjects. [**node classification**]
    * baseline: GCN
    * Result
1. Reddit
    * Task: classify posts to different conmmunity
    * baseline: GraphSAGE
    * Result
1. PPI
    * Task: classify protein function
    * baseline: GAT/GraphSAGE

## [Round2] Introspect (before reading the interpretation section)

## [Round2] Other Review [Survey/Twitter/OpenReview/]

## [Round1] Summary
From the phenomenon of GCN(deeper the layer, worse the performance), the author mathematicly
prove both the node attributes and the subgraph structure effect hidden state. Thus different
scales of neighborhood aggregation is needed. So they propose the jump connection between
different layer. The key idea is simple but the math foundation is built solidly.

## [Round1&2] Ref (Further reading && Comparing with this work)
1. Deep Learning on Graphs: A Survey. Ziwei Zhang, Peng Cui, Wenwu Zhu. 2018

