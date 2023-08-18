Exclusion flowcharts
================

The aim of this script is to make exclusion flowcharts for different
clinical scenarios and outcomes. The number of patients in each group is
copied from a secure server for sensitive data (not available here).
Start by loading the library.

``` r
library(PRISMAstatement)
```

    Warning: package 'PRISMAstatement' was built under R version 4.2.3

Next, make an exclusion flowchart for the **base clinical model with
overall survival** as outcome:

``` r
flow_exclusions(incl_counts = c(1736, 1589, 1564, 1447), total_label = "Total Screened",
    incl_labels = c("Curative setting", "Early disease or locoregionally advanced disease",
        "Outcome available"), excl_labels = c("Recurrence/Metastatic setting", "Metastatic disease",
        "Missing outcome"), percent_of_total = TRUE)
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/base%20clinical%20OS-1.png)<!-- -->

Similarly for the **base clinical model with disease-free survival** as
outcome:

``` r
flow_exclusions(incl_counts = c(1736, 1589, 1564, 1251), total_label = "Total Screened",
    incl_labels = c("Curative setting", "Early disease or locoregionally advanced disease",
        "Outcome available"), excl_labels = c("Recurrence/Metastatic setting", "Metastatic disease",
        "Missing outcome"), percent_of_total = TRUE, labelloc = "t", label = "test")
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/base%20clinical%20dfs-1.png)<!-- -->

Next the flowchart for **GS1, GS2 and GS3 and overall survival**. These
use the same subset of data, but GS3 has different variable encoding.

### STOPPED here

``` r
flow_exclusions(incl_counts = c(1736, 1589, 1564, 1251), total_label = "Total Screened",
    incl_labels = c("Curative setting", "Early disease or locoregionally advanced disease",
        "Outcome available"), excl_labels = c("Recurrence/Metastatic setting", "Metastatic disease",
        "Missing outcome"), percent_of_total = TRUE, labelloc = "t", label = "test")
```

![](Exclusion_flowcharts_markdown_files/figure-gfm/GS1%20GS2%20GS3%20OS-1.png)<!-- -->
