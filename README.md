# hotspot_spatial_workflow
Expects spatial in obsm part of anndata object 

where spatial can be populated using the following: 
given X and Y are stored in the metadata obs. 

``` 
coords = np.array((anndata.obs["X"],anndata.obs["Y"]))
anndata.obsm["spatial"] = coords.T 
``` 

Run squidpy spatial neighbors 

```
import squidpy as sq
adata_spatial_neighbor = sq.gr.spatial_neighbors(
    anndata, coord_type="generic", delaunay=True
)
```

# From Hotspot documentation

Alternative choices for 'model'
The model is used to fit per-cell expectations for each gene assuming no correlations. This is used as the null model when evaluating autocorrelation and gene-gene local correlations. The choices are:

danb: 'Depth-adjusted negative binomial' (aka NBDisp model) from M3Drop
bernoulli: Here only the detection probability for each gene is estimated. Logistic regression on gene bins is used to evaluate this per-gene and per-cell as a function of the cells umi_count value.
normal: Here expression values are assumed to be normally-distributed and scaled by the values in umi_count.
none: With this option, the values are assumed to be pre-standardized 