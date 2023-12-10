Joyce Robbins
2023-12-10

# redav

**This version adds `num_char`, `max_rows` and `max_cols` parameters to
`plot_missing()`. To install use:**

``` r
remotes::install_github("jtr13/redav", ref = "limit")
```

This package will eventually contain functions, data, and templates to
accompany data visualization courses.

If you encounter problems or have questions, please open an
[issue](https://github.com/jtr13/redav/issues) or start/contribute to a
[discussion](https://github.com/jtr13/redav/discussions).

As of now, it contains two functions: `draw_biplot()` and
`plot_missing()`.

There are other options for drawing biplots in the **ggplot2**
framework; `ggbiplot()` in the [**ordr**
package](https://github.com/corybrunson/ordr) is an excellent choice.
The main contributions of `draw_biplot()` are ease of use and option to
calibrate only one of the axes. Calibration calculations are performed
by `calibrate()` in the [**calibrate**
package](https://cran.r-project.org/web/packages/calibrate/index.html).

Currently, `draw_biplot()` takes a data frame, performs principal
components analysis (PCA) on the numeric columns using `prcomp()` and
draws a biplot using the first non-numeric column as labels for the
principal component scores (points). Additional options besides PCA may
be added in the future.

`plot_missing()` was designed as a replacement for `extracat::visna()`
which is no longer available on CRAN. It has improved labeling and the
option to label axes as percents or numbers.

## Examples

### `draw_biplot()`

``` r
library(redav)
draw_biplot(attitude)
```

![](Readme_files/figure-gfm/unnamed-chunk-3-1.svg)<!-- -->

``` r
draw_biplot(attitude, key_axis = "raises") + 
  ggplot2::ggtitle("The Chatterjee-Price Attitude Data", 
          sub = "package: datasets (base R)")
```

![](Readme_files/figure-gfm/unnamed-chunk-3-2.svg)<!-- -->

``` r
s77 <- as.data.frame(state.x77)
s77$state_name <- rownames(s77)
draw_biplot(s77)
```

![](Readme_files/figure-gfm/unnamed-chunk-3-3.svg)<!-- -->

``` r
draw_biplot(s77, key_axis = "Murder", ticklab = 0:16, project = FALSE,
            point_color="lightblue") + ggplot2::theme_classic()
```

![](Readme_files/figure-gfm/unnamed-chunk-3-4.svg)<!-- -->

``` r
draw_biplot(s77, mult = 1, point_color = "pink")
```

![](Readme_files/figure-gfm/unnamed-chunk-3-5.svg)<!-- -->

``` r
draw_biplot(s77, points = FALSE)
```

![](Readme_files/figure-gfm/unnamed-chunk-3-6.svg)<!-- -->

### `plot_missing()`

``` r
library(redav)
data(CHAIN, package = "mi")
plot_missing(CHAIN)
```

![](Readme_files/figure-gfm/unnamed-chunk-4-1.svg)<!-- -->

``` r
plot_missing(CHAIN, percent = FALSE)
```

![](Readme_files/figure-gfm/unnamed-chunk-4-2.svg)<!-- -->

``` r
plot_missing(CHAIN, max_rows = 4)
```

![](Readme_files/figure-gfm/unnamed-chunk-4-3.svg)<!-- -->

``` r
plot_missing(CHAIN, max_cols = 3)
```

![](Readme_files/figure-gfm/unnamed-chunk-4-4.svg)<!-- -->

``` r
plot_missing(CHAIN, num_char = 5)
```

![](Readme_files/figure-gfm/unnamed-chunk-4-5.svg)<!-- -->

``` r
plot_missing(mtcars)
```

![](Readme_files/figure-gfm/unnamed-chunk-4-6.svg)<!-- -->

*Rendered from* `Readme.Rmd`.
