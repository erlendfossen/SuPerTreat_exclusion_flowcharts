Exclusion flowcharts
================

The aim of this script is to make exclusion flowcharts for different
clinical scenarios and outcomes. The number of patients in each group is
copied from a secure server for sensitive data
(“04_flowchart_eligibility.R”, not available here). Start by loading the
library.

``` r
library(PRISMAstatement)
```

    Warning: package 'PRISMAstatement' was built under R version 4.2.3

``` r
library(manipulateWidget)
```

    Warning: package 'manipulateWidget' was built under R version 4.2.3

Next, make an exclusion flowchart for the **base clinical model with
overall survival** as outcome:

``` r
flow_exclusions(incl_counts = c(1589, 1564, 1447), total_label = "Total Screened",
    incl_labels = c("Early disease or locoregionally advanced disease", "Outcome available"),
    excl_labels = c("Metastatic disease / missing TNM stage", "Missing outcome"),
    percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/base%20clinical%20OS-1.png)<!-- -->

Similarly for the **base clinical model with disease-free survival** as
outcome:

``` r
flow_exclusions(incl_counts = c(1589, 1564, 1251), total_label = "Total Screened",
    incl_labels = c("Early disease or locoregionally advanced disease", "Outcome available"),
    excl_labels = c("Metastatic disease / missing TNM stage", "Missing outcome"),
    percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/base%20clinical%20dfs-1.png)<!-- -->

Next the flowchart for **GS1, GS2 and GS3 and overall survival**. These
use the same subset of data, but GS3 has different variable encoding.

``` r
flow_exclusions(incl_counts = c(1589, 1230, 1206, 1097), total_label = "Total Screened",
    incl_labels = c("Gene expression available", "Early disease or locoregionally advanced disease",
        "Outcome available"), excl_labels = c("Missing gene expression", "Metastatic disease / missing TNM stage",
        "Missing outcome"), percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/GS1%20GS2%20GS3%20OS-1.png)<!-- -->

The flowchart for **GS1, GS2 and GS3 and disease-free survival** is very
similar. Note that SCANDARE is also excluded at the outcome stage due to
DFS information being very low quality (same for other flowcharts).
These also use the same subset of data, but GS3 has different variable
encoding.

``` r
flow_exclusions(incl_counts = c(1589, 1230, 1206, 907), total_label = "Total Screened",
    incl_labels = c("Gene expression available", "Early disease or locoregionally advanced disease",
        "Outcome available"), excl_labels = c("Missing gene expression", "Metastatic disease / missing TNM stage",
        "Missing outcome"), percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/GS1%20GS2%20GS3%20DFS-1.png)<!-- -->

Next the flowchart for **GS4 & GS5 and overall survival**. These use the
same subset of data, but have different variable encoding for chemo
agents. These are also only for Locoregionally advanced disease and
require information about treatment (specifically chemotherapy agents if
they had chemotherapy).

``` r
flow_exclusions(incl_counts = c(1589, 1230, 1012, 802, 750), total_label = "Total Screened",
    incl_labels = c("Gene expression available", "Locoregionally advanced disease",
        "Treatment information available", "Outcome available"), excl_labels = c("Missing gene expression",
        "Early disease or metastatic disease", "Missing treatment information", "Missing outcome"),
    percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/GS4%20GS5%20OS-1.png)<!-- -->

Lastly, the flowchart for **GS4 & GS5 and disease-free survival**. These
use the same subset of data, but have different variable encoding for
chemo agents. Very similar to OS above.

``` r
flow_exclusions(incl_counts = c(1589, 1230, 1012, 802, 700), total_label = "Total Screened",
    incl_labels = c("Gene expression available", "Locoregionally advanced disease",
        "Treatment information available", "Outcome available"), excl_labels = c("Missing gene expression",
        "Early disease or metastatic disease", "Missing treatment information", "Missing outcome"),
    percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/GS4%20GS5%20DFS-1.png)<!-- -->

Finally, combine two flow charts into one figure: **clinical base model
OS & GS4&GS5 OS data**.

``` r
# clinical base:
clinical_flow <- flow_exclusions(incl_counts = c(1589, 1564, 1447), total_label = "Total Screened",
    incl_labels = c("Early disease or \nlocoregionally advanced disease", "Outcome available"),
    excl_labels = c("Metastatic disease \n or missing TNM stage", "Missing outcome"),
    percent_of_total = TRUE)

# GS4&GS5 OS:
GS4GS5_flow <- flow_exclusions(incl_counts = c(1589, 1230, 1012, 802, 750), total_label = "Total Screened",
    incl_labels = c("Gene expression available", "Locoregionally advanced disease",
        "Treatment information available", "Outcome available"), excl_labels = c("Missing gene expression",
        "Early disease \nor metastatic disease", "Missing treatment \ninformation",
        "Missing outcome"), percent_of_total = TRUE)

combineWidgets(clinical_flow, GS4GS5_flow, ncol = 2, nrow = 1)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/clinical%20GS4%20GS5%20OS-1.png)<!-- -->

``` r
# OBS: this failed on RMarkdown, but works fine in R itself... Can export the
# figure directly from R.
```
