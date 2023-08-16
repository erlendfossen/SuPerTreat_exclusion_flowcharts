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

    PhantomJS not found. You can install it with webshot::install_phantomjs(). If it is installed, please make sure the phantomjs executable can be found via the PATH variable.

<div id="htmlwidget-7f4157ba4a8e8e9eb392" style="width:672px;height:480px;" class="grViz html-widget"></div>
<script type="application/json" data-for="htmlwidget-7f4157ba4a8e8e9eb392">{"x":{"diagram":"\n    digraph prisma {\n    node [shape=\"box\" ];\n    graph [splines=ortho, nodesep=1 ]\n    \nTotalScreened [label=\"Total Screened\n972 (100%)\"];\nConsented_A [label=\"Consented\n132 (13.6%)\"];\nCompletedStudy_B [label=\"Completed Study\n 77 (7.9%)\"];\nBMI30_C [label=\"BMI 30\n 14 (1.4%)\"];\nDeclinedConsent_a [label=\"Declined Consent\n840 (86.42%)\"];\nFailedtoComplete_b [label=\"Failed to Complete\n 55 (5.66%)\"];\nBMI30_c [label=\"BMI 30\n 63 (6.48%)\"];\nTotalScreened -> {Consented_A; DeclinedConsent_a};\nConsented_A -> {CompletedStudy_B; FailedtoComplete_b};\nCompletedStudy_B -> {BMI30_C; BMI30_c};\n{rank=same; TotalScreened DeclinedConsent_a}\n{rank=same; Consented_A FailedtoComplete_b}\n{rank=same; CompletedStudy_B BMI30_c}\n}","config":{"engine":"dot","options":null}},"evals":[],"jsHooks":[]}</script>
