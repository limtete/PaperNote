## Paper
A Review of Relational Machine Learning for Knowledge Graphs

## Outline
1. knowledge graph/knowledge base
    1. knowledge representation
        1. DF:
            1. model information in the form of entities and relationship
            1. a collection of facts with type hierarchies and type constraints for
            the purpose of machine-readable data
        1. Semantic Web/LinkData/RDF
        1. description language: SPO triple (subject, predicate, object)
    1. interpretation of non-existing triples in KG:
        1. CWA: non-exist --> false
        1. OWA: non-exist --> unknown but may true
    1. construction method
        1. curated: high quality, limited scale
        1. collaborative: high quality, less limited scale(still not enough for BigData)
        1. automated semi-structured: medium quality, large scale(not enough)
        1. automated unstructured: lowest quality, enough scale
    1. KB types
        1. Schema-based: disambiguated, but fixed/limited world
        1. Schema-free: ambiguated, but unfixed/unlimited world
    1. Usage
        1. search engine: text-based --> semantic result
        1. QA
        1. Specific domain: QA/decision support
    1. KGC specific task
        1. link prediction
        1. entity resolution
        1. link-based clustering: community detection in social network[54]
1. statistical relational learning
    1. KG in probabilistic form: **tensor representation of binary relational data**
        > frankly speaking, i don't think this is a good idea for representation
    1. KG's probabilistic property:
        1. homophily: things related tends to share similar characteristic
        1. block structure
        1. long-range statistical dependency
        1. skewed prior distribution: because of its incompleteness
    1. Types of SRL models: variant kinds of probabilistic independency
        1. conditionally independent given latent features
        1. conditionally independent given observed graph features
        1. local interactions between triples - Markov Random Field
    > All of the three are discriminative model
1. latent feature models
    > key intuition: the relationships between entities can be derived from interactions of their latent features
    1. RESCAL
    1. Tensor factorization models
    1. Matrix factorization methods
    1. Multi-layer perceptrons: E-MLP, ER-MLP
    1. Neural tensor networks
    1. Latent distance models: TransE
1. graph feature models
    > explains triples directly from the observed triples in the knowledge graph
    1. Similarity measures for uni-relational data
    1. Rule Mining and Inductive Logic Programming
        > this is what intelligence mean, as BaoJie suggests
    1. Path Ranking Algorithm
1. combination of latent-based and graph-based
1. training method for KG
1. Markov Random Field
1. Example: Knowledge Vault
    * Building step:
        1. extract from Web
        1. train models on Freebase: ER-MLP, PRA
        1. ensemble models to do lin prediction
1. Future work
    1. Non-binary relation
    1. Hard constraints
    1. Generalization to new entities/relations
    1. Querying probabilistic KG
    1. Trustworthiness of KG
## Reference reOrganization
* SRL: [1,2,3]
* knowledge representation: [11,19,20]
* Semantic Web/LinkData/RDF: [14,15,16]
* HIN: [21]
* automated unstructured approaches via ML/NLP: [9]
* OpenIE tech: [37]
* Link Prediction: [45, 46]
