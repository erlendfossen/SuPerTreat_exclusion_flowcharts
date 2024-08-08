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
    excl_labels = c("Distant metastasis / missing TNM stage", "Missing outcome"),
    percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/base%20clinical%20OS-1.png)<!-- -->

Similarly for the **base clinical model with disease-free survival** as
outcome:

``` r
flow_exclusions(incl_counts = c(1589, 1564, 1251), total_label = "Total Screened",
    incl_labels = c("Early disease or locoregionally advanced disease", "Outcome available"),
    excl_labels = c("Distant metastasis / missing TNM stage", "Missing outcome"),
    percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/base%20clinical%20dfs-1.png)<!-- -->

Next the flowchart for **GS1, GS2 and GS3 and overall survival**. These
use the same subset of data, but GS3 has different variable encoding.

``` r
flow_exclusions(incl_counts = c(1589, 1230, 1206, 1097), total_label = "Total Screened",
    incl_labels = c("Gene expression available", "Early disease or locoregionally advanced disease",
        "Outcome available"), excl_labels = c("Missing gene expression", "Distant metastasis / missing TNM stage",
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
        "Outcome available"), excl_labels = c("Missing gene expression", "Distant metastasis / missing TNM stage",
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
        "Early disease or distant metastasis", "Missing treatment information", "Missing outcome"),
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
        "Early disease or distant metastasis", "Missing treatment information", "Missing outcome"),
    percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/GS4%20GS5%20DFS-1.png)<!-- -->

Finally, combine two flow charts into one figure: **clinical base model
OS & GS4&GS5 OS data**.

``` r
# clinical base:
clinical_flow <- flow_exclusions(incl_counts = c(1589, 1564, 1447), total_label = "Total Screened",
    incl_labels = c("Early disease or \nlocoregionally advanced disease", "Outcome available"),
    excl_labels = c("Distant metastasis \n or missing TNM stage", "Missing outcome"),
    percent_of_total = TRUE)

# GS4&GS5 OS:
GS4GS5_flow <- flow_exclusions(incl_counts = c(1589, 1230, 1012, 802, 750), total_label = "Total Screened",
    incl_labels = c("Gene expression available", "Locoregionally advanced disease",
        "Treatment information available", "Outcome available"), excl_labels = c("Missing gene expression",
        "Early disease \nor distant metastasis", "Missing treatment \ninformation",
        "Missing outcome"), percent_of_total = TRUE)

combineWidgets(clinical_flow, GS4GS5_flow, ncol = 2, nrow = 1)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/clinical%20GS4%20GS5%20OS-1.png)<!-- -->

``` r
# OBS: this failed on RMarkdown, but works fine in R itself... Can export the
# figure directly from R.
```

## June2024

Add two more flowcharts, starting from OS GS1. First **OS only RT**:

``` r
flow_exclusions(incl_counts = c(1589, 1230, 1206, 1097, 752), total_label = "Total Screened",
    incl_labels = c("Gene expression available", "Early disease or locoregionally advanced disease",
        "Outcome available", "Received radiotherapy"), excl_labels = c("Missing gene expression",
        "Distant metastasis / missing TNM stage", "Missing outcome", "Did not recieve radiotherapy or \nmissing information about radiotherapy"),
    percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/OS%20only%20RT-1.png)<!-- -->

Second **OS only CT**:

``` r
flow_exclusions(incl_counts = c(1589, 1230, 1206, 1097, 936, 445), total_label = "Total Screened",
    incl_labels = c("Gene expression available", "Early disease or locoregionally advanced disease",
        "Outcome available", "Locoregionally advanced disease", "Received systemic treatment"),
    excl_labels = c("Missing gene expression", "Distant metastasis / missing TNM stage",
        "Missing outcome", "Early disease", "Did not recieve systemic treatment or \nmissing information about systemic treatment"),
    percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/OS%20only%20CT-1.png)<!-- -->

Lastly, save as jpeg file with 300 dpi resolution:

``` r
library(DiagrammeRsvg)
library(rsvg)


flow <- flow_exclusions(incl_counts = c(1589, 1230, 1206, 1097), total_label = "Total Screened",
    incl_labels = c("Gene expression available", "Early disease or locoregionally advanced disease",
        "Outcome available"), excl_labels = c("Missing gene expression", "Distant metastasis / missing TNM stage",
        "Missing outcome"), percent_of_total = TRUE, width = 680, font_size = 8)

PRISMAstatement:::prisma_pdf(flow, "test_pdf.pdf")
```
