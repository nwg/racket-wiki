*DRAFT*
This page hopes to describe the plan for the Continuous Integration process to use in Racket.

**Goal**: to ensure Racket is and remains to be a reliable system, without unexplained regressions or performance changes.

# Contributing

If you are interested in contributing machines, volunteering with code, or anything else, get in touch. We gather in channel #ci on Slack.

# Support Tiers

Due to available resources for testing and benchmarking, there are X support tiers. 
TODO: decide how many support tiers are available and which arch/vm/os/options are in each tier.

# Environments

This section describes the environment (hardware/software combinations) on which we can guarantee that Racket works.

## Racket Support Matrix

Architecture names, operating system names, and their valid combinations are defined by the [$GOOS and $GOARCH](https://golang.org/doc/install/source#environment) variables used by the [Go](https://golang.org/) compiler.

TODO: Some racket features, such as memory accounting, require specifying certain options when compiling Racket. How do we test that these features work on supported platforms? Does it count as a separate variant of racket? The compiled racket binary is different and could behave differently.

### Racket (CGC and 3M)

|      | `linux` | `darwin` | `windows` |
| ---- | ----- | ------ | ------- |
| `386`  |       |        |         |
| `amd64` | | | | 
| `arm` | | | |
| `arm64` | | | |
| `mips` | | | |
| `mipsle` | | | |
| `mips64` | | | |
| `mips64le` | | | |
| `ppc64` | | | |
| `ppc64le` | | | |
| `s390x` | | | |

TODO
TODO Where does QNX and FreeBSD fit in?

### Racket (CS)

|      | `linux` | `darwin` | `windows` |
| ---- | ----- | ------ | ------- |
| `386`  |       |        |         |
| `amd64` | | | | 
| `arm` | | | |
| `arm64` | | | |
| `mips` | | | |
| `mipsle` | | | |
| `mips64` | | | |
| `mips64le` | | | |
| `ppc64` | | | |
| `ppc64le` | | | |
| `s390x` | | | |

TODO

# GitHub Actions

We are committed to using GitHub Actions for CI as it provides an unparalleled level of integration with our current workflow.

# Dashboard

The long-term plan is to develop a single-page dashboard that gather information from test runs and benchmarks and displays it in a succing and understandable way so that Racket devs know at-a-glance what the status of the project is.