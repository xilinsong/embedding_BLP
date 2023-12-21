# embedding_BLP
An extention on BLP with product embeddings.

### Motivation
Traditional BLP method by [Berry et al. (1995)](https://doi.org/10.2307/2171802) are able to capture consumers' heterogeneous tastes by including the interaction between consumer demographics and product attributes, but the interaction is parametric and it requires detailed information about consumers. 

Inspired by what businesses do for recommendations, we propose using high-dimensional product embeddings to capture heterogeneous tastes. Embeddings can reveal nonparametric relationships among products, and consumers with product purchase history provides the context for identifying product embeddings.

We incorporate product embeddings into BLP framework while keeping both product attributes and user demographics (if available). Product attributes provide side information to the embeddings that can be effective when the product is new to the market.

We use an Enhanced Graph Embedding with Side information (EGES) model to get the embeddings, and test if it works for the fake cereal data in Nevo (2000). Future steps are to apply the model on a larger dataset and to compare outcomes with BLP.

### Flow
We use the EGES model from [Wang et al. (2018)](https://arxiv.org/abs/1803.02349). Product embeddings are the coordinates of the products in a high-dimensional space. Consumers buy products that are more preferred and related. By looking at the purchase history of consumers, we can locate the products and find out the relationship among products. The key steps are as follows:

1.  Use consumer purchase histories to build a graph of products. The nodes represent the products and the edges identify whether the two nodes are both purchased by the same consumer. The graph will be directed and weighted: the direction of the edge preserves the chronological order of purchasing, the weights of the edges represents the frequency of co-purchasing the two connected nodes.
2.  Simulate `node2vec` random walks from the graph. This creates sequences of products, whose connections are supported by consumers in our dataset.
3.  Perform `Skip-Gram` algorithm on the sequences to get the embeddings of the product. The final embedding of a product will be a weighted average of the product itself and the corresponding product attributes.
4.  Users are represented as the average of their purchased products, so that we can get the similarities between consumers and products. This replaces the non-linear preference part in BLP.
