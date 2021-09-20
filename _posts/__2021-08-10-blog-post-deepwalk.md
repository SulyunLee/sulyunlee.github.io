---
title: 'Understanding DeepWalk'
date: 2021-08-10
permalink: /posts/deepwalk
tags:
  - network embedding
  - representation learning
  - skipgram
  - deepwalk
---

Network embedding is learning representations of nodes in a network. The benefit of network embedding is that each node can be represented as a lower-dimensional vector space, which is useful as feature vectors for several tasks, such as link prediction, node classification, node clustering, and anomaly detection etc.
Many machine-learning tasks on networks become easier when network embeddings are adopted because the feature engineering process which is specific to certain datasets or tasks is not required. 

DeepWalk <sup>[1](#paper)</sup> is one of the most popular network embedding approach that uses unsupervised way of learning node embeddings. Unsupervised node embedding approach is learning the representations of nodes by preserving the desired properties of network and optimizing the embeddings that meets the objective function.	Among the various properties of networks, DeepWalk preserves the closeness of nodes. In other words, node embeddings learned by DeepWalk are similar if nodes are close to each other in a network. Therefore, node embeddings contain the information of topological network structures.

Here are the steps of DeepWalk algorithm:
1. Random walk to generate contexts of nodes
2. Use Skip-gram model
-----
## 1. Random walk
Random walk is sequentially sampling nodes to generate the context of nodes. 
 
 
 
## 2. Skip-gram model


-----
### Python codes

<a name="paper">[1]</a>    Perozzi, B., Al-Rfou, R., & Skiena, S. (2014, August). Deepwalk: Online learning of social representations. In Proceedings of the 20th ACM SIGKDD international conference on Knowledge discovery and data mining (pp. 701-710).

