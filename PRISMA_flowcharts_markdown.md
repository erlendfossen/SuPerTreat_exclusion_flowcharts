PRISMA flowcharts
================

Start by loading the library.

``` r
library(PRISMAstatement)
```

    Warning: package 'PRISMAstatement' was built under R version 4.2.3

Next, make an exclusion flowchart for the base clinical model with
overall survival as outcome:

``` r
flow_exclusions(incl_counts = c(972, 132, 77, 14), total_label = "Total Screened",
    incl_labels = c("Consented", "Completed Study", "BMI 30"), excl_labels = c("Declined Consent",
        "Failed to Complete", "BMI 30"), percent_of_total = TRUE)
```

![](PRISMA_flowcharts_markdown_files/figure-gfm/base%20clinical%20OS-1.png)<!-- -->
