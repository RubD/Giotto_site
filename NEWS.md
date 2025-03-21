
# Please use the new website [www.giottosuite.com](https://drieslab.github.io/Giotto_website/). This website is outdated and archived for consistency with the original Giotto publication (Dries et al, Genome Biology, 2021).

# Giotto 1.0.1 - 1.0.3

- Fixed bugs
- Added seed to HMRF
- Created functions to read 10X Visium .h5 files
  - see **createGiottoVisiumObject** to create a Giotto object
    directly  
  - see **get10Xmatrix_h5** to extract the count matrix

# Giotto 1.0.0

This is the first major release of Giotto. If you still want to work
with the previous version, then you can find the older releases
[here](https://github.com/RubD/Giotto/tags).

Here is an overview about what has changed in the meantime:

- **NEW:** Addition of **getSpatialDataset** to directly download a
  spatial dataset  
  (expression matrix, spatial coordinates and metadata). This is now
  also included in the examples that you can find under the **Datasets**
  tab on this website.

- **NEW:** We have added tools to install, remove and check a Giotto
  r-miniconda environment. This miniconda environment is one way to make
  sure that you can run functions that require Python modules.

  - **installGiottoEnvironment**: (re-)installs a Giotto miniconda
    environment  
  - **removeGiottoEnvironment**: removes a Giotto miniconda
    environment  
  - **checkGiottoEnvironment**: verifies if a Giotto environment can be
    found

The other alternative is to
[install](https://rubd.github.io/Giotto_site/articles/installation_issues.html#python-manual-installation)
them in your own favorite Python environment and provide the path in the
**createGiottoInstructions** command.

- extension and improvement of spatial gene detection methods:

  - **NEW:** addition of **spark** method  
  - improvements for silhouetteRank:
    - faster implementation  
    - multi parameter version as **silhouetteRankTest**
  - improvements for binSpect:
    - faster implementation  
    - multi parameter version: **binSpectSingle** or **binSpectMulti**

- Spatial cell type enrichment methods have been streamlined and updated

  - **runPAGEEnrich** to run enrichment using PAGE algorithm and
    selected marker genes  
  - **runRankEnrich** to run enrichment using a whole expression
    matrix  
  - **runHyperGeometricEnrich** to run enrichment using the
    hypergeometric test

- **NEW:** Spatial cell type deconvolution has been added:

  - use **runSpatialDeconv** or **runDWLSDeconv**

- **NEW:** Addition of **addCellIntMetadata** to add information about
  interacting cell types, which can subsequently be viewed with the
  spatPlot commands.

- **NEW:** Addition of 3 small vignettes that cover different types of
  spatial datasets:

  - single-cell resolution ([mini
    seqFISH+](../articles/mini_seqfish.html))
  - multi-cell resolution ([mini
    visium](../articles/mini_visium.html))  
  - 3D dataset ([mini STARmap](../articles/mini_starmap.html))
  - See **data(package = ‘Giotto’)**

- Cell Proximity Genes has been changed to Interaction Changed Genes

  - This better reflects the nature of gene changes due to neighboring
    cell interactions
  - CPG functions are deprecated and will be removed in the future

- Several function help pages have been updated with dummy example
  code  

- several small and big fixes to the code

# Giotto 0.3.5

- background images See [howto’s](../articles/howto_images.html)
- support for sparse matrices  
- PCA can be calculated with the packages irlba (default) or factominer
  (old default)
- complemented PCA with separate functions for a scree plot and
  jackstraw plot
- addition of **readExprMatrix** to read an expression matrix
- addition of **addGenesPerc** to add information about genesets
  (e.g. mitochondrial genes)
- addition of **showGrids** and **showNetworks** to see available
  spatial grids and networks
- several bug fixes

# Giotto 0.3.2

- added voronoi plots to use in spatial plotting. See
  [howto’s](../articles/howto_voronoi_plots.html)  
- generalized visualization parameters between functions

# Giotto 0.3.1

- (optional) automatic installation of python modules through
  reticulate:
  - you can provide your preferred python path
  - the giotto environment can be installed automatic
  - if you do not provide the python path and do not choose to install
    the giotto environment, then it will take the default python path  
- several bug fixes
- several mini-datasets are now included within Giotto for quick
  testing:
  - field 1 of seqFISH+ (single-cell)
  - the visium brain Dentate Gyrus subset (spots)
  - subset of starMAP (3D)

example to acces the seqFISH+ mini dataset:

``` r
# raw counts
small_seqfish_expr_matrix = read.table(system.file("extdata", "seqfish_field_expr.txt", package = 'Giotto'))
# cell locations
small_seqfish_locations = read.table(system.file("extdata", "seqfish_field_locs.txt", package = 'Giotto'))
```

# Giotto 0.3.0

- Default spatial network created with **createSpatialNetwork** is now a
  Delaunay spatial network.

``` r
# to create the old default kNN spatial network use:
createSpatialKNNnetwork(gobject)

# or use this function with the following setting
createSpatialNetwork(gobject, method = 'kNN')
```

- The function names for extracting spatial genes have changed:

``` r
# binGetSpatialGenes is now:
binSpect(gobject) # binary Spatial extraction

# spatial_genes_python is now:
silhouetteRank(gobject)
```

- Fixed multiple bugs
- Improved speed by changing code to Rcpp and implementing
  parallelization options
- updated [howto’s](../articles/getting_started.html) tutorials in Start
  section
- Finished the analysis of 10 different spatial datasets (tutorials are
  a work-in-progress)

# Giotto 0.2.4

- New examples on mouse kidney and brain using the recently released
  [10X Visium
  datasets](https://www.10xgenomics.com/spatial-transcriptomics/)
  (**NEW**)
- Added tools to identify spatial enrichment based on cell-type specific
  gene signature lists (**NEW**)

# Giotto 0.2.3

- New example with 3D-like spatial data of the mouse hypothalamic
  preoptic region using
  [merFISH](https://science.sciencemag.org/content/362/6416/eaau5324)
  (**NEW**)  
- New example with 3D spatial data
  [STARmap](https://science.sciencemag.org/content/361/6400/eaat5691)
- New example with the highly sensitive data from
  [osmFISH](https://www.nature.com/articles/s41592-018-0175-z)
- New example on the Cerebellum with the scalable data from
  [Slideseq](https://science.sciencemag.org/content/363/6434/1463)
- New example on mouse olfactory bulb using immobilized primers on glass
  slides from [Spatial
  Transcriptomics](https://science.sciencemag.org/content/353/6294/78)
- Updated seqFISH+ cortex example (**NEW**)
- Updated STARmap cortex example (**NEW**)

# Giotto 0.2.2

- Implemented [SpatialDE](https://github.com/Teichlab/SpatialDE) and
  [trendsceek](https://github.com/edsgard/trendsceek)
- Updated support for 3D spatial data  
- Added support for the use of global instructions and automatically
  saving your plots (**NEW**)
- Add wrapper for differential expression with
  [MAST](https://github.com/RGLab/MAST) and
  [SCRAN](https://bioconductor.org/packages/release/bioc/html/scran.html)
