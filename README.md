_*<sub>to be continued</sub>_

My experimental module using a common _centroid-based_ clustering.

![image](https://github.com/fevpallar/MeanBasedClusteringModule/assets/17115595/777983bd-5adf-4d55-ac42-96cda1680041)



It looks really bad actually. I mean look at the resulting plot (*).

_* Still under construction_
  
---

Background

It's just _k-means_ at its essence. 

The very first constraint is defined as

(For each data point $n$, the sum of $z_{nk}$ over all clusters k should be 1)

```math
\sum_{k=1}^{K} z_{nk} = 1
```
Where $z_{nk}$ is 1 if data point $n$ is assigned to cluster $k$ and $0$ otherwise.

This notation is used (because) it's just that they way data is represented (the arrangement) here is like


<pre>
Data point 	k1  k2
X1	        1  0
X2	        0  1
X3             ..  ..
</pre>

So that when doing $\sum z_{nk}x_{n}$ only the points assigned to the cluster $k$ will be included.

And the centroid is defined as

```math
\mu_{k} =\sum z_{nk}x_{n} / \sum z_{nk}
```

The objective of the clustering is defined as the minimum of

```math
\sum_{n=1}^{N}\sum_{k=1}^{K}z_{nk}(x_{n}-\mu_{k})^{T} (x_{n}-\mu_{k})
```

So if there are 3 centroids defined then it takes

```math
\sum_{n=1}^{N} z_{n1} (x_{n} - \mu_{1})^{T} (x_{n} - \mu_{1}) + \sum_{n=1}^{N} z_{n2} (x_{n} - \mu_{2})^{T} (x_{n} - \mu_{2}) + \sum_{n=1}^{N} z_{n3} (x_{n} - \mu_{3})^{T} (x_{n} - \mu_{3})
