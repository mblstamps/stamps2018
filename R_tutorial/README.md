# STAMPS 2018 R Tutorials 

Welcome! This subdirectory contains R Tutorials for STAMPS 2018 @ MBL. 

1. Make sure you have downloaded R and RStudio.

2. Download gfortran, which is needed for certain R packages and will make your life much easier in the future! Link: https://gcc.gnu.org/wiki/GFortranBinaries

3. Open RStudio.

4. Set your filepath to a location on your computer that you in which you are comfortable saving files using:
``` r
setwd("YOUR FILEPATH HERE")
```

5. Run the following code in the R console: 
``` r
utils::download.file("https://github.com/mblstamps/stamps2018/blob/master/R_tutorial/R_tutorial.zip?raw=true", "R_tutorial.zip")
utils::unzip("R_tutorial.zip")
```

6. Move into the working directory that was created:
``` r
setwd("STAMPS2018")
```

7. Before moving on, check to make sure you have 7 ".R" files and 2 ".txt" files:
``` r
list.files()
```

8. If you have that, then load in the data we'll be using for this tutorial:
``` r
covariates <- read.csv("FWS_covariates.txt", sep = "\t")
abundances <- read.csv("FWS_OTUs.txt", sep = "\t", row.names = 1, header = T)
```

9. Next, install all the packages we will be needing:
``` r 
install.packages("dplyr")
install.packages("magrittr")
install.packages("devtools")
install.packages("ggplot2")
source("https://bioconductor.org/biocLite.R")
biocLite("phyloseq")
install.packages("parallel")
install.packages("foreach")
install.packages("doParallel")
devtools::install_github("adw96/breakaway")
```

10. You are now set up! The tutorials are set up in the following order:
``` 
1_loops.R
2_apply.R
3_functions.R
4_lists.R
5_sourcesystem.R
6_parallel.R
7_markdown.R 
```

Happy coding!
