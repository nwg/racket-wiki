# Math Library Features

# Requested Features

Not sure how to run this yet. Nominations? An informal voting system? Free-for-all?

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
 * improve performance for prime? for small primes

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
* Array unfolds (should be able to define list-array->array with them)

## math/matrix

* Review, fiddle, document
* Add constructor (matrix ((1 2) (3 4)))

## math/statistics

* Expose Walker table functions used in discrete-dist
* Covariance/correlation matrices

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
