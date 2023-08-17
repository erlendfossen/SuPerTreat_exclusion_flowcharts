PRISMA flowcharts
================

The aim of this script is to make PRISMA flowcharts for different
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

![](PRISMA_flowcharts_markdown_files/figure-gfm/base%20clinical%20OS-1.png)<!-- -->

Similarly for the **base clinical model with disease-free survival** as
outcome:

``` r
flow_exclusions(incl_counts = c(1736, 1589, 1564, 1251), total_label = "Total Screened",
    incl_labels = c("Curative setting", "Early disease or locoregionally advanced disease",
        "Outcome available"), excl_labels = c("Recurrence/Metastatic setting", "Metastatic disease",
        "Missing outcome"), percent_of_total = TRUE, labelloc = "t", label = "test")
```

![](PRISMA_flowcharts_markdown_files/figure-gfm/base%20clinical%20dfs-1.png)<!-- -->
