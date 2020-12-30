geoaxe
======



[![cran checks](https://cranchecks.info/badges/worst/geoaxe)](https://cranchecks.info/pkgs/geoaxe)
[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](http://www.repostatus.org/badges/latest/active.svg)](http://www.repostatus.org/#active)
[![R-CMD-check](https://github.com/ropensci/geoaxe/workflows/R-CMD-check/badge.svg)](https://github.com/ropensci/geoaxe/actions?query=workflow%3AR-CMD-check)
[![codecov.io](https://codecov.io/github/ropensci/geoaxe/coverage.svg?branch=master)](https://codecov.io/github/ropensci/geoaxe?branch=master)
[![rstudio mirror downloads](http://cranlogs.r-pkg.org/badges/geoaxe)](https://github.com/r-hub/cranlogs.app)
[![cran version](http://www.r-pkg.org/badges/version/geoaxe)](http://cran.rstudio.com/web/packages/geoaxe)

`geoaxe` - split geospatial objects into pieces

## Install

Stable CRAN version


```r
install.packages("geoaxe")
```

Development version


```r
pak::pkg_install("ropensci/geoaxe")
```


```r
library("geoaxe")
library("sp")
```

## Spatial Polygons and friends input

Works for only `SpatialPolygons` for now, but aim to include related classes soon.


```r
library("rgeos")
wkt <- "POLYGON((-180 -20, -140 55, 10 0, -140 -60, -180 -20))"
poly <- rgeos::readWKT(wkt)
polys <- chop(x = poly)
```

Plot original polygon


```r
plot(poly, lwd = 6)
```

![plot of chunk unnamed-chunk-6](inst/img/unnamed-chunk-6-1.png)

Add chopped up polygon bits


```r
plot(polys, add = TRUE)
```

![plot of chunk unnamed-chunk-7](inst/img/unnamed-chunk-7-1.png)



## Well-Known Text input


```r
wkt <- "POLYGON((-180 -20, -140 55, 10 0, -140 -60, -180 -20))"
plot(chop(wkt))
```

![plot of chunk unnamed-chunk-9](inst/img/unnamed-chunk-9-1.png)



## Manipulate number of cells

> plots go left to right, then down, and repeat


```r
layout(matrix(c(1,2,3,4), 2, 2, byrow = TRUE))
par(mar = c(1, 0, 1, 0))
plot(chop(wkt, n = 10))
plot(chop(wkt, n = 15))
plot(chop(wkt, n = 20))
plot(chop(wkt, n = 50))
```

![plot of chunk unnamed-chunk-11](inst/img/unnamed-chunk-11-1.png)



## Manipulate cell size

> plots go left to right, then down, and repeat


```r
layout(matrix(1:8, 4, 2, byrow = TRUE))
par(mar = c(1, 0, 1, 0))
plot(chop(wkt, size = 2))
plot(chop(wkt, size = 4))
plot(chop(wkt, size = 8))
plot(chop(wkt, size = 15))
plot(chop(wkt, size = 25))
plot(chop(wkt, size = 50))
plot(chop(wkt, size = 100))
plot(chop(wkt, size = 200))
```

![plot of chunk unnamed-chunk-13](inst/img/unnamed-chunk-13-1.png)



## Meta

* Please [report any issues or bugs](https://github.com/ropensci/geoaxe/issues).
* License: MIT
* Please note that this package is released with a [Contributor Code of Conduct](https://ropensci.org/code-of-conduct/). By contributing to this project, you agree to abide by its terms.
