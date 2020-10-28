---
layout: post
title: "Graph Embeddings on Riemannian Manifolds"
categories: Deep Learning
---

[arxiv: Computationally Tractable Riemannian Manifolds for Graph Embeddings](https://arxiv.org/abs/2002.08665)

This article is about the work of graph embedding on Riemannian manifolds. The embedding algorithm on two matrix manifolds (SPD manifold (manifold with non-positive curvature) and Grassmann manifold (manifold with non-negative curvature)) is given and their performances are better than the previous hyperbolic embedding and elliptical embedding. The author claims that these enhancements in embedding performances give new evidence for the importance of non-Euclidean embeddings in machine learning.

The main embedding method is to optimize an SNE loss function extended to Riemannian manifolds through the method of gradient descent, the purpose is to keep the original graph structure as much as possible during the embedding process.
On the SPD manifold, the author compares two metrics, Stein divergence, and canonical distance.
Experimental results show that embedding on the two manifolds is better than traditional methods in most cases.

I believe that this method gives a new idea of ​​data dimensionality reduction. Traditional PCA or t-SNE usually maps the data to the Euclidean space, while this method maps the data to a low-dimensional manifold when keeps the original graph structure unchanged. 
In practical applications, the point set on the low-dimensional manifold can be projected onto the tangent space of a certain point (for example, logarithmic mapping is used on matrix manifolds), which is more conducive to distance calculation or visualization; while in high-dimensional Euclidean space the point set can be represented in a graph by constructing k-NN or other methods, and then the dimensionality reduction method could be applied.
This is especially applicable in certain scenarios that mainly rely on the neighbor structure.