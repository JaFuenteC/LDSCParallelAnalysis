# paLDSC: Parallel Analysis based on Multivariate Linkage Disequilibrium Score Regression (LDSC)

The paLDSC function allows to identify the number of non-spurious dimensions in exploratory genomic factor analysis. The method adapts a classic method known as Parallel Analysis (Horn, 1965) to the genomic spaces. The method compares the eigenvalues generated from the eigen decomposition of the LDSC-derived genetic correlation matrix to the eigenvalues of a Monte-Carlo simulated null correlation matrix with random noise drawn from the multivariate LDSC sampling distribution. The suggested number of components to be extracted corresponds with the last component with a larger eigenvalue than 95% of the eigen values observed for the corresponding component from the null correlation matrix.

The mandatory arguments of the paLDSC function are S_Stand and V_Stand, corresponding with the standardized genetic covariance and sampling distribution matrices from the LDSC output (S and V matrices, respectively, which can be obtained by setting stand = TRUE in the LDSC function). 
The following optional arguments are also implemented:

1. r: defines the number of replications for the Monte-Carlo simulations of null correlation matrices (500 by default).

2. p: defines the percentile for the simulated eigen-values (.95 by default).

3. diag: defines whether diagonallized PA should be conducted (FALSE by default). Diagonallized PA assumes uncorrelated sampling errors for the simulated null correlation matrices, as would happen if the data were pure noise. Thus, if diag = TRUE, the function will only use the diagonal of the sampling distribution V (i.e., the sampling variances or the phenotypes in the original genetic correlation matrix) to introduce variation in the simulated null correlation matrices. If diag = FALSE (by default), the whole multivariate sampling distribution LDSC V matrix will be used to simulate the null.

4. fa: defines whether the eigenvalues should also be computed from a common factor solution from a explotory factor analysis of n factors (by default 1) using the factor method fm (by default minimum residual). By default this argument is set to FALSE, since there is some degree of variation on the factor analysis eigenvalues depending on the number of factors extracted.

5. fm: factor method for the exploratory factor analysis if fa = T (by default minimum residual).

6. nfactors: number of factors to be extracted in the exploratory factor analysis if fa = T (by default = 1).

7. save.pdf: whether the scree-plots derived from the PA function should be saved into a .pdf file.
