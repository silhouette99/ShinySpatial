# ShinySRT

========

### Description
`ShinySRT` an interactive and sharable Shiny-based web application for spatially resolved transcriptomics. It is designed to process various prevalent formats of spatial transcriptome data, enabling the creation of an interactive interface tailored for comprehensive data analysis.The interactive interface created by ShinySpatial is entirely open-source and is amenable to extensive customization to align with the specific requirements of the user.

===========

### Features
> Written in R, using a shiny application that generates an interactive interface that can be mounted to a server or shared on the web.
> It supports several major spatial transcriptome data formats (Seurat (Visim and image-based-spatial)/SpatialExperiment (and SingleCellExperiment)/h5ad), in addition to specific list imports.
> Multiple spatial transcriptome slice samples data can be imported into shiny web app.
> Customizing spatial spot annotations and and spot selection
> Multivariate comparisons. Analyzing the change in the dependent variable with the independent variable in different groups
> Visualization images and data sheet downloads
> One-step generation of the shiny interface, shiny app is completely open source and can be customized

==============

### Content and Guide
The basic workflow is that `ShinySRT` generates the required configuration files and shiny app code by utilizing spatial transcriptome data objects.
We use a 10x spatial transcriptome data within the lab as an example to demonstrate the operation and content of `ShinySRT` with the following code.

``` r
library(ShinySpatial)

makespashiny(dat,title = 'ShinySRT exmaple')
```
Run one line of code, a new directory called '/shinyspatial_app' will be created in the current directory, where the shiny app exists, and where the user can call `shiny::runApp` to run the app locally in Rstudio.In addition, it is possible to use the server's app remotely by mounting the shiny app's directory in the `/srv/shiny-server` directory of the server that has the proxy. In addition, the app can be used remotely by mounting the shiny app directory in the `/srv/shiny-server` directory of a server with a proxy. shiny apps can also be deployed to other web platforms in other ways [shinyapps.io](https://www.shinyapps.io/)


The shiny app generated by `ShinySRT` consists of six main modules, with the module names shown in the leftmost menu bar in the figure. At the bottom of the menu bar, there is an input field for importing annotations for new spots.

The current display is the first module "SpotInfo vs GeneExpr", which mainly shows the relationship between the annotation information of spatial spots and gene expression. Switch the annotation information of the spots by the drop-down menu at "Spot information" and select the displayed genes by the drop-down menu at "Gene expression". On the right hand side is the area for customized spot selection which can be used to select the area by drawing circle or clicking, and it need to name the annotation area before selecting.

![](image/content1.png)

For storing new annotation information, you need to first create a column name for this group of annotation information, and then stored in the form of columns in the following figure in the metadata list, the list can be downloaded and exported, and then use this annotation can be copied from the column and pasted in the left input area. metadata on the right side of the gene in the display of the expression of the spots information statistics.

![](image/content2.png)

The second module "GeneExpr vs GeneExpr" focuses on the relationship between the spatial expression of two genes, in the same way as the selection of spots in the first module.

![](image/content3.png)

In addition to this, Module 4 demonstrates the relationship between two genes by the spatial co-determination of two genes in the same slice sample. Thresholds for gene expression can be set using the sliders on the right, and the table below shows the statistics for the co-determination of the genes.

![](image/content4.png)

The third module, "Viol / Box data chart", plots traditional statistical box and violin plots based on the annotation information and gene expression or scoring of the spot, showing the relationship between the annotation information and genes.

![](image/content5.png)

The fourth module, "Portion data chart", shows the proportion of one grouping of information over another, e.g., the proportion or number of seurat subgroups in each anatomical region of the brain, with most of the spots in the HT region belonging to the four subgroups.

![](image/content6.png)

The sixth module shows the expression of genes in different regions by means of "bubble charts or heatmaps", which can also be clustered in rows and columns respectively.

![](image/content7.png)
===================
