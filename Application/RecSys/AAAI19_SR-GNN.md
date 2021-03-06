# [Session-based Recommendation with Graph Neural Network](https://arxiv.org/pdf/1811.00855.pdf)
---

## [Round1] Big Que(What the whole field are concerned about)
Session-based Recommendation
> Predict user actions based on anoymous sessions.

## [Round1] Background(< 5 sentences)
**keywords**: interactions
1. Session-based
1. Markov chains
    > disad: strong independence assumption
1. RNNs
    > dis-ad1: need adquate user profile <br>
    > dis-ad2: model single-way transition between consecutive items

## [Round1] Specific Que
model complex transitions among distant items

## [Round1] Approach(What are the authors going to do)
1. build directed graph
1. use GGsNNs to get node embedding
1. get session representation by combining global preference 
$\mathbf{s}_{\mathrm{g}}$ and current interest $\mathbf{s}_{\mathrm{l}}$
1. for each session, predict item of next click.

## [Round1] Methodology

<img src="../../img/sr_gnn.png" width="70%" height="70%">

1. construct a session graph
    * item set: <span style="color:#E37F14">$V = \left\{v_{1}, v_{2}, \dots, v_{m}\right\}$</span>
    * session sequence: <span style="color:#E37F14">$s = \left[v_{s, 1}, v_{s, 2}, \dots, v_{s, n}\right]$</span>
    * session graph: <span style="color:#E37F14">$\mathcal{G}_{s}=\left(\mathcal{V}_{s}, \mathcal{E}_{s}\right)$</span>
        * node represents i-th clicked item of item set V in session $s$: <span style="color:#E37F14">$v_{s, i} \in V$</span>
        * edge represents two continuous clicks in session $s$: <span style="color:#E37F14">$\left(v_{s, i-1}, v_{s, i}\right) \in \mathcal{E}_{s}$</span>
1. learn node vector embedding $v_{s, n}$: using GGNNs.
    * Notation:
        * $\mathbf{H} \in \mathbb{R}^{d \times 2 d}$: weight matrix of GRU.
        * $z_{s, i}$ and $r_{s, i}$: reset and update gates of GRU.
        * $\mathbf{A}_{s} = \left[\mathbf{A}_{s}^{(out)},\mathbf{A}_{s}^{(in)}\right] \in \mathbb{R}^{n \times 2 n}$: connection matrix.
> For node $v_{s,i}$ of graph $\mathcal{G}_{s}$,<br>
> $\begin{aligned} \mathbf{a}_{s, i}^{t} &=\mathbf{A}_{s, i :}\left[\mathbf{v}_{1}^{t-1}, \ldots, \mathbf{v}_{n}^{t-1}\right]^{\top} \mathbf{H}+\mathbf{b} \\ \mathbf{z}_{s, i}^{t} &=\sigma\left(\mathbf{W}_{z} \mathbf{a}_{s, i}^{t}+\mathbf{U}_{z} \mathbf{v}_{i}^{t-1}\right) \\ \mathbf{r}_{s, i}^{t} &=\sigma\left(\mathbf{W}_{r} \mathbf{a}_{s, i}^{t}+\mathbf{U}_{r} \mathbf{v}_{i}^{t-1}\right) \\ \widetilde{\mathbf{v}}_{i}^{t} &=\tanh \left(\mathbf{W}_{o} \mathbf{a}_{s, i}^{t}+\mathbf{U}_{o}\left(\mathbf{r}_{s, i}^{t} \odot \mathbf{v}_{i}^{t-1}\right)\right) \\ \mathbf{v}_{i}^{t} &=\left(1-\mathbf{z}_{s, i}^{t}\right) \odot \mathbf{v}_{i}^{t-1}+\mathbf{z}_{s, i}^{t} \odot \mathbf{v}_{i}^{t} \end{aligned}$

1. construct session embedding: attention mechanism.<br>
Given session $s=\left[v_{s, 1}, v_{s, 2}, \dots, v_{s, n}\right]$

    * local session embedding: $\mathbf{s}_{l} = \mathbf{v}_{n}$
    * global session embedding $\mathbf{s}_{g}$: 
    >$\begin{aligned} \alpha_{i} &=\mathbf{q}^{\top} \sigma\left(\mathbf{W}_{1} \mathbf{v}_{n}+\mathbf{W}_{2} \mathbf{v}_{i}+\mathbf{c}\right) \\ \mathbf{s}_{\mathrm{g}} &=\sum_{i=1}^{n} \alpha_{i} \mathbf{v}_{i} \end{aligned}$
    * hybrid embedding $\mathbf{s}_{\mathrm{h}}=\mathbf{W}_{3}\left[\mathbf{s}_{1} ; \mathbf{s}_{\mathrm{g}}\right]$
    * Notation:
        * parameters: $\mathbf{q} \in \mathbb{R}^{d}$, $\mathbf{W}_{1}, \mathbf{W}_{2} \in \mathbb{R}^{d \times d}$ and $\mathbf{W}_{3} \in \mathbb{R}^{d \times 2 d}$, controls weight and compress $\mathbf{s}_{l}$ and $\mathbf{s}_{g}$ into latent space $\mathbb{R}^{d}$

1. Make recommendation and model training
    * recommendation score over all candidate items: $\hat{\mathbf{z}}_{i}=\mathbf{s}_{\mathrm{h}}^{\top} \mathbf{v}_{i}$
    * probabilities of nodes appearing in next clicks: $\hat{\mathbf{y}}=\operatorname{softmax}(\hat{\mathbf{z}})$
    * loss func: $\mathcal{L}(\hat{\mathbf{y}})=-\sum_{i=1}^{m} \mathbf{y}_{i} \log \left(\hat{\mathbf{y}}_{i}\right)+\left(1-\mathbf{y}_{i}\right) \log \left(1-\hat{\mathbf{y}}_{i}\right)$

## [Round1] Result
1. Datasets
    * yoochoose: only use recent 1/4 and 1/64 part of the dataset
    * diginetica
1. Evaluation metrics
    * Precision@K:
    > <img src="../../img/confuse_matrix.png" width="70%" height="70%">
    * Mean reciprocal rank(MRR):  evaluating any process that produces a list of possible responses to a sample of queries, ordered by probability of correctness.
    > $\mathrm{MRR}=\frac{1}{|Q|} \sum_{i=1}^{|Q|} \frac{1}{\operatorname{rank}_{i}}$
1. Subtask
    1. graph-build variant: normalized global connection vs. full connection vs.normalized connection matrix
    > prove connection matrix usefull
    1. different session: local only vs. average pooling vs. global by attention vs. local+global
    > prove combine $\mathbf{s}_{g}$ and $\mathbf{s}_{l}$ is useful.

## [Round2] Introspect (before reading the interpretation section)

## [Round2] Other Review [Survey/Twitter/OpenReview/]

## [Round1] Summary
This work focuses on **session-based recommendation**. "Session-based" means that there is no user profile or user history information,
only item information and item clickd lists are available. This kind of recommendation often happens in anonymous situation. Previous works 
face the problem of failing to model complex click interaction among items. This problem is partly solved in this work by constructing item 
interaction graph, then use GNN to compute item embedding; with item embedding, session embedding formed by attention mechinism from two different perspect: local and global.<br>
The main contribution of this paper, i think, is the **graph building** way. From methodology aspect, this work use graph neural network to solve session-based recommendation. GNN + KG + RecSys seems to be a good aspect to form new idea. <br>
Several aspects remains to be considered:
1. node attribution like item attributes.
1. item information knowledge graph.

## [Round1&2] Ref (Further reading && Comparing with this work)
> <img src="../../img/sr_gnn_baseline.png" width="30%" height="30%">
