*DRAFT*
This page hopes to describe the plan for the Continuous Integration process to use in Racket.

**Goal**: to ensure Racket is and remains to be a reliable system, without unexplained regressions or performance changes.

# Contributing

If you are interested in contributing machines, volunteering with code, or anything else, get in touch. We gather in channel #ci on Slack.

# Support Tiers

Due to available resources for testing and benchmarking, there are X support tiers. 
TODO: decide how many support tiers are available and which arch/vm/os/options are in each tier.

# CI Environments

This section describes the CI environments (hardware/software combinations) on which we can guarantee that Racket works.

## Implementation details

All CI workflows live in [racket/.github/workflows](https://github.com/racket/racket/tree/master/.github/workflows):

* `ci-pr.yml`: This workflow is ran for each Pull Request. It is a fast workflow that attempts to test most common configurations and OSes. Its goal is to give confidence to the reviewers and the PR author that the code does not break Racket.
* `ci-push.yml`: This workflow is slightly slower than the PR workflow but more methodical in its testing. It does take longer to run but it also provides a higher confidence that the racket repo is still in good shape.
* `ci-nightly.yml` (TODO): This workflow is slow but ran once a day (nightly in Flatt's timezone). It is thorough and gives the highest confidence that the repo remains green in all tested configurations.

*Note*: There is a possibility that a commit, passes the PR but breaks Push or even passes both PR and Push workflows but breaks nightly. Since we do not want a red state in the repo - the policy is to revert the commit and open a bug report assigned to the commiter of the broken build so that it can be fixed and re-committed.

### The Standard Test Set

Whenever running tests, we sometimes refer to the standard test set or `Test (std.)`. These are not all the available tests but those deemed to be most relevant. At the moment these are (which have a dependency on `racket-test` and `db-test` packages):

```
        raco test -l tests/racket/test
        racket -l tests/racket/contract/all
        raco test -l tests/json/json
        raco test -l tests/file/main
        raco test -l tests/net/head
        raco test -l tests/net/uri-codec
        raco test -l tests/net/url
        raco test -l tests/net/url-port
        raco test -l tests/net/encoders
        raco test -l tests/openssl/basic
        raco test -l tests/openssl/https
        raco test -l tests/match/main
        raco test -l tests/zo-path
        raco test -c tests/xml
        raco test -l tests/db/all-tests
        raco test -c tests/stxparse
```

### Pull Request CI

Build:
|         | `linux` | `darwin` | `windows` |
| ------- | ------- | -------- | --------- |
| `amd64` | cgc,3m  | cgc,3m   | cgc,3m,cs | 

Test (std.):
|         | `linux` | `darwin` | `windows` |
| ------- | ------- | -------- | --------- |
| `amd64` |   3m    |    3m    |     3m    | 

## Racket Support Matrix

Architecture names, operating system names, and their valid combinations are defined by the [$GOOS and $GOARCH](https://golang.org/doc/install/source#environment) variables used by the [Go](https://golang.org/) compiler.

- [@jackfirth](https://github.com/jackfirth) Some racket features, such as memory accounting, require specifying certain options when compiling Racket. How do we test that these features work on supported platforms? Does it count as a separate variant of racket? The compiled racket binary is different and could behave differently.

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

- [@jackfirth](https://github.com/jackfirth) For reference, Go just flat out [doesn't](https://github.com/golang/go/issues/23633) [support](https://github.com/golang/go/issues/12045) QNX at all. We should see how other languages handle this.

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