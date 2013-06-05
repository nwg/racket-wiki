# Math Library Features

# Requested Features

Not sure how to run this yet. Nominations? An informal voting system? Free-for-all?

* [Automatic Differentiation](http://en.wikipedia.org/wiki/Automatic_differentiation)
* Data Tables like Python's [PANDAS](http://pandas.pydata.org/) library
* [Mondrian](http://stats.math.uni-augsburg.de/mondrian/) style dynamic, interactive data analysis visualizations (this probably belongs in plotting library, but needs to be integrated with the data table above)

# Planned Features

Please don't edit this section. Neil or Jens Axel will move things here from Requested Features.

The to-do lists in each subsection are roughly in priority order.

## math/base

* New functions
 * logb (high-accuracy log with base)
 * floor-logb (exact, take from plot)
 * ceiling-logb (exact, take from plot)

## math/flonum

* Document double-double flonum operators (e.g. fl2+ : Flonum Flonum Flonum Flonum -> (Values Flonum Flonum))
* New functions
 * flmodulo
 * flremainder

## math/special-functions

 * Arithmetic-geometric mean (agm)
 * Bessel functions, first kind: besj0, besj1, besj (see math/bigfloat for naming convention)
 * Bessel functions, second kind: besy0, besy1, besy (see math/bigfloat for naming convention)

## math/number-theory

 * in-primes

## math/bigfloat

* New functions
 * bfremainder
 * bfmodulo
* Firm up private functions used to test math/special-functions, make them public
 * Log-space arithmetic
 * Beta
 * Incomplete gamma
 * Incomplete beta
 * Hurwitz zeta

## math/array

* Efficient functional update
 * Sparse-Array type
 * array-set, array-indexes-set, array-slice-set

## math/matrix

* matrix-row-space
* matrix-null-space, matrix-left-null-space
 * Use QR or SVD for inexact matrices; see http://scicomp.stackexchange.com/questions/1861/understanding-how-numpy-does-svd
* S+N decomposition
* Linear least squares problems (data fitting)
* Pseudo inverse
* Eigenvalues and eigenvectors
* Operator (induced) norms, condition numbers

## math/statistics

* Expose Walker table functions used in discrete-dist
* Covariance/correlation matrices
* Principal Component Analysis
* Common regression algorithms (linear, general linear, polynomial)
* Common, robust hypothesis testing algorithms

## math/distributions

* Unordered distributions
 * Dirichlet
 * Multivariate normal
* Integer distributions
 * Multinomial
 * Categorical (values are 0-based indexes)
 * Hypergeometric
* Real distributions
 * Student t
 * Kernel density estimate (KDE)
 * Generalized gamma (special cases: gamma, Weibull, log-normal)
 * Laplace
 * F
 * Fisher
 * Pareto
 * Von Mises
 * chisqr-dist (easy wrapper around gamma-dist)
