# pvclust-using-bray-curtis-and-unifrac-index
this script incorperate different distance/dissimilarity index (bray-curtis, jaccard, weighted and unweighted unifrac) to R pvclust package.
here are examples:

```R
library(downloader)
library(MASS)
library(ape)
source("/path/to/pvclust_bcdist.R")

data(Boston, package = "MASS")

# to use bray-curtis dissimilarity, choose method.dist="bray"
result <- pvclust(Boston, method.hclust="ward", method.dist="bray", n=100)
plot(result)

# to use jaccard index, choose method.dist="jaccard"
result2 <- pvclust(Boston, method.hclust="ward", method.dist="jaccard", n=100)

# to use weighted or unweighted unifrac distance metric
count_table=read.table("a.mothur.subsampled.count_table",header=T)
count_table=count_table[,-2]
count_table=data.frame(count_table[,-1],row.names = as.vector(count_table[,1]))
tree=read.tree("Newick.tre") #Newick format file from e.g. Mothur clearcut() function, it has to be named as 'tree'

result3 <- pvclust(count_table, method.hclust="ward", method.dist="unweighted", n=100)
result4 <- pvclust(count_table, method.hclust="ward", method.dist="weighted", n=100)
```
