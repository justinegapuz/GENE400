# GENE400
R codes that were used to visualise the expression levels of TRP channels from a single-cell RNA seq dataset

# 1. Install the following packages
install.packages(‘ggplot2’)

install.packages(‘Seurat’)

install.packages(‘cowplot’)

install.packages(‘Matrix’)

# 2. Load the libraries
library(ggplot2

library(Seurat)

library(cowplot)

library(Matrix)

# 3. Set the directory
On R, set your working directory to the esmo.combine.rds file location
The code below will work if your folder is on the desktop and inside the Single_cell_codes_of_B_diegensis folder

Setwd(“~/Desktop/Single_cell_codes_of_B_diegensis”)

# 4. Load the rds data
Double-click on esmo.combined.rds to open with Rstudio
Or you can load with the code below
emso.combined <- readRDS("~/Desktop/Single- cell_codes_of_B_diegensis/emso.combined.rds") 




# Visualisation of target gene expression
To visualise the expression of the target gene using scRNA seq dataset.


# 1. Load the whole dataset with the code below
Dimplot(esmo.combined, reduction = “umap”, label = T)

# 2. Set the assay to RNA with the code below
DefaultAssay(esmo.combined)<-“RNA

# 3. Open the Stringtie_annotations excel file and look for channel of interest
#For example, look for a MSTRG with the gene ID of your target gene (e.g., g11140)

# 4. Once you have obtained the MSTRG of interest. Enter the code below
ggpubr::annotate_figure(

  p = FeaturePlot(emso.combined, features = "MSTRG.11700", order=TRUE),
  
  top = ggpubr::text_grob(label = 'Bd_g11140/TRPA', face = 'bold',))

# 5. We can then load the expression level of the channel of interest with the code below.
ggpubr::annotate_figure(

   p = VlnPlot(emso.combined, features = "MSTRG.11700"),
  
   top = ggpubr::text_grob(label = 'Bd_g11140/TRPA', face = 'bold'))
  

# 6. To compare the expression of the different channels and look at which clusters they are expressed, we can create a dot plot by using the code below.
For example:

features <- c("MSTRG.11700", "MSTRG.11523", "MSTRG.2065", "MSTRG.644", "MSTRG.9561", "MSTRG.13654")

DotPlot(emso.combined, features = features) + RotatedAxis()













