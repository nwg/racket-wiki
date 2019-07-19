This page hopes to describe the plan for the Continuous Integration process to use in Racket.

**Goal**: to ensure Racket is and remains to be a reliable system, without unexplained regressions or performance changes.

# Support Levels

Due to available resources for testing and benchmarking, there are three support levels implemented. 

In support level 1, all tests and benchmarks are ran on a per-commit basis. This should be fast and thorough enough to catch most obvious errors. In support level 2, we run all the tests and benchmarks on a wider variety of architectures. In support level 3, we run not on all supported architectures, but also with all supported compilers.

# Environments

This section describes the environment (hardware/software combinations) on which we can guarantee that Racket works.

## Racket Support Matrix

Valid names for architectures and operating systems defined by [Golang](https://golang.org/doc/install/source#environment).

### Racket (CGC and 3M)

|      | linux | darwin | windows |
| ---- | ----- | ------ | ------- |
| 386  |       |        |         |
| amd64 | | | | 
| arm | | | |
| arm64 | | | |
| ppc64 | | | |
| ppc64le | | | |
| mips | | | |
| mipsle | | | |
| mips64 | | | |
| mips64le | | | |
| s390x | | | |

TODO

### Racket (CS)

|      | linux | darwin | windows |
| ---- | ----- | ------ | ------- |
| 386  |       |        |         |
| amd64 | | | | 
| arm | | | |
| arm64 | | | |
| ppc64 | | | |
| ppc64le | | | |
| mips | | | |
| mipsle | | | |
| mips64 | | | |
| mips64le | | | |
| s390x | | | |

TODO

# GitLab CI

TODO

# Dashboard

The long-term plan is to develop a single-page dashboard that gather information from test runs and benchmarks and displays it in a succing and understandable way so that Racket devs know at-a-glance what the status of the project is.