
<!-- README.md is generated from README.Rmd. Please edit that file -->

# The effectiveness of population-wide screening in reducing SARS-CoV-2 infection prevalence in Slovakia

This repository contains the data and code for our manuscript:

Pavelka S, Van-Zandvoort K, Abbott S, Sherratt K, Majdan M, CMMID
COVID-19 working group, Jarčuška P, Krajčí M, Flasche S*, Funk S* (\*:
equal contribution), *The effectiveness of population-wide screening in
reducing SARS-CoV-2 infection prevalence in Slovakia*. Available at
<https://cmmid.github.io/topics/covid19/Slovakia.html>.

### How to download or install

You can download the compendium as a zip from from this URL:
<https://github.com/sbfnk/covid19.slovakia.mass.testing/archive/master.zip>.

Or you can install this compendium as an R package,
`covid19.slovakia.mass.testing`, from GitHub with:

``` r
# install.packages("devtools")
remotes::install_github("sbfnk/covid19.slovakia.mass.testing")
```

### Included data sets

The repository contains three data sets:

The testing data set `ms.tst` can be loaded with

``` r
data(ms.tst)
```

Incidence of cases confirmed by PCR per county `PCR.inc` can be accessed
with

``` r
data(PCR.inc)
```

The `Rt.county` data set contains the estimated median reproduction
number in each county on 22 October 2020.

``` r
data(Rt.county)
```

This data set can be re-created using the The
[EpiNow2](https://epiforecasts.io/EpiNow2/) R package by running (noting
that it can take a long time to run depending on the hardware
available).

``` r
source(here::here("data-raw", "scripts", "rt.r"))
source(here::here("data-raw", "scripts", "convert_data.r"))
```

The [EpiNow2](https://epiforecasts.io/EpiNow2/) R package that is used
to estimate the reproduction numbers uses generation times and delay
distributions saved in `data-raw/data`. They can be re-generated by
running.

``` r
source(here::here("data-raw", "scripts", "rt-distributions.r"))
```

The Google mobility data set for Slovakia `mob.slo` visualised in
Supplementary Figure S4 can be accessed with

``` r
data(mob.slo)
```

### Figures and tables

To regenerate Table 1, run

``` r
county_table("table1.pdf")
```

To regenerate Fig. 1, run

``` r
pcr_incidence()
```

To regenerate Fig. 2, run

``` r
rr <- risk_ratios()
rr$figures$a
rr$figures$b
rr$tables
```

To generate Table S1 and estimate the adjusted prevalence ratio, run

``` r
r <- regression()
```

To regenerate Fig. S4, run

``` r
mobility()
```

To regenerate Fig. S6, run

``` r
bed_occupancy()
```

To regenerate Fig. S7, run

``` r
prevalence()
```

### Minimum specificity

To estimate minimum specificity, run

``` r
estimate_min_specificity()
#> [1] 0.9984521
```
