# [Discrete Social Recommendation](https://www.aaai.org/Papers/AAAI/2019/AAAI-LiuC.2795.pdf)
---

## [Round1] Big Que(What the whole field are concerned about)
1. RecSys considering social information to solve cold start/data sparsity
1. computational efficiency in terms of time and space

## [Round1] Background(< 5 sentences)
**keywords**: low resource
1. Matrix factorization
    > expensive storage and computation cost
1. binarize latent features + hamming space
    > 2-stage method.<br>
    > not capable of preserving the original data geometry in the real-value space

## [Round1] Specific Que
computation speed && storage

## [Round1] Approach(What are the authors going to do)
1. unified framework
1. balanced and uncorralated constraints
    > guide DSR to get informative yet compactive binary code
1. optimization algorithm

## [Round1] Methodology
steps:
1. preliminary: MF in real space with social info
    > Assumption: user-item rating matrix and user-user relation matrix share same user latent space
1. Binary code with balanced && decorralated constraints
    > This is generally NP hard
1. constraints softening:
    1. using continuous vector to represent constraints
    1. using tr() to approximate d()

``` CSS

--> (Q1) data sparsity/cold start
--> (S1) side info: social info
    --> (Q2) inefficiency in time/space
    --> (S2) Binary code + Hamming Space
        --> (Q3) quantation loss: fail to preserve geometrical property
        --> (A3) Balanced/de-correlated constraint
            --> (Q4) general NP hard
            --> (A4) soften binary in real space
```

## [Round1] Result
1. Datasets
![DSR_dataset.png](attachment:DSR_dataset.png)
1. Evaluation metrics
    1. [Normalized Discounted Cumulative Gain(NDCG)](https://machinelearningmedium.com/2017/07/24/discounted-cumulative-gain/)
    1. Recall
1. Subtask
    1. Performance
        1. In-matrix recommendation
            * Res1: CFSR > DSR > CFSRB $\approx$ DCF
        1. out-matrix recommendation(cold start)
            * CFSR > DSR > CFSRB
        > the more data used, the more narrow gap between CFSR and DSR
    1. Sensitivity analysis of hyperparameters
    1. Time/Memory usage comparision

## [Round2] Introspect (before reading the interpretation section)

## [Round2] Other Review [Survey/Twitter/OpenReview/]

## [Round1] Summary
The problem this paper aims to solve is efficiency of time/space computation. Based on previous work in binary code, they
mainly contribute in 3 aspects:
1. unified framework for simultaneously combining user-item rating and user-user social relation, different from aforementioned
   works which divides learning binary code into 2 steps and thus suffers from failing to preserve geometric properties. In this
   way can geometric attributes of user-item rating matrix and user-user socail relation matrix be preserved.
1. a learning algorithm is developed which involves softened balanced/decorrelated constraint.
    1. By balanced/de-correlated constraint, binary code can be informative and compative;
    1. By "soften", binary code learning which in general is NP hard can be learnt
1. 2 experiment of 3 datasets is conducted, one focusing on performance(measured by NDCG@K and Recall@K), the other on effciency.
   when performance is almost same with SOTA, the efficiency of DSR can be 5 times faster, and 1/37 memory is needed .
Its **introduction** part draws clear clues from general matrix factorization to the specific question the author targeted. Also clear 
is the development of learning method.

## [Round1&2] Ref (Further reading && Comparing with this work)

