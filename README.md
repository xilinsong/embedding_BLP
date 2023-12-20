# embedding_BLP
An extention on BLP with product embeddings.

### Motivation
Traditional BLP method by Berry, Levinsohn, and Pakes (1995) are able to capture consumers' heterogeneous tastes by including the interaction between consumer demographics and product attributes, but the interaction is parametric and it requires detailed information about consumers. 

Inspired by what businesses do for recommendations, we propose using high-dimensional product embeddings to capature heterogeneous tastes. Embeddings can reveal nonparametric relationships among products, and consumers with product purchase history provides the context for identifying product embeddings.

We incorporate product embeddings into BLP framework while preserving both product attributes and user demographics (if available). Product attributes provide side information to the embeddings that can be effective when the product is new to the market.

We use an Enhanced Graph Embedding with Side information (EGES) model to get the embeddings, and test if it works for the fake cereal data in Nevo (2000). Future steps are to apply the model on a larger dataset and to compare outcomes with BLP.

