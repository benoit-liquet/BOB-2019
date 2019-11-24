Bayes on the Beach Workshop 2019
================================

Workshop Aims:
--------------

-   Explore Bayesian Variable Selection methods for group structure data
-   Some coding in R 
-   Analysis of two Genetics Data Set

## Genomics Data: Wide Data, High Dimensional Data

![](wide_data.png) \

We have too many variables, prone to overfitting.
Need to remove variable, or regularize, or both 

- \textcolor{red}{Main constraint:} situation with $p>n$ 

- \textcolor{red}{Strong colinearity} among the variables.



## Group structures within the data 

- \textcolor{red}{Genomics}: genes within the same pathway have similar functions and act together in regulating a biological system. 

$\hookrightarrow$ These genes can add up to have a larger effect 

$\hookrightarrow$ can be detected as a group (i.e., at a pathway or gene set/module level).



\textcolor{blue}{We consider variables are divided into groups:}

```math
- \small{Example $p$: SNPs grouped into $K$ genes}
\footnotesize{$$\mathbf{X}=[\underbrace{SNP_1,\ldots+SNP_k}_{gene_1}|\underbrace{SNP_{k+1},SNP_{k+2},\ldots,SNP_{h}}_{gene_2}|\ldots|\underbrace{SNP_{l+1},\ldots,SNP_{p}}_{gene_K}]$$}

- \textcolor{red}{Example $p$: genes grouped into $K$ pathways/modules} ($X_j=\textrm{gene}_j$)
$$\mathbf{X}=[\underbrace{X_1,X_2,\ldots,X_k}_{M_1}|\underbrace{X_{k+1},X_{k+2},\ldots,X_{h}}_{M_2}|\ldots|\underbrace{X_{l+1},X_{l+2},\ldots,X_{p}}_{M_K}]$$
```

## Application Rat Data: Aim and Data 

- \textcolor{red}{Identify a parsimonious set of predictors} that explains the \textcolor{blue}{joint variability of gene expression} in four tissues (adrenal gland, fat, heart, and kidney).

- 770 SNPs in 29 inbred rats as a predictor matrix (n = 29, p = 770)
- 29 measured expression levels in the 4 tissues as the outcome (q = 4).

```{r}
load("RAT.RData")
X <- RAT$X
Y <- RAT$Y
MAP.file <- RAT$MAP.file
gsize <- RAT$gsize
dim(X)
dim(Y)
```

