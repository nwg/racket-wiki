# Racket CI Meet

Date: November 21, 2019
Present: Jack Firth, Paulo Matos

Each section presents a topic discussed. 

## Racket Dashboard

Long-term goal would be to have a Racket CI system based on GitHub Actions (referred to as Actions for the remainder of the report), and a visualization dashboard for the CI system based in Racket. Because we are in such an early phase with implementing the CI based on Actions, we simply discussed how it could work. 

1. CI system sends information to a webapp using an HTTP API (to be defined);
2. This app ensures the information comes from an authenticated source and stores in the information in a database;
3. The dashboard queries the database and presents the relevant information;

One possible prototype to start with would be to have CI save the time it took to build Racket in each different configuration and start by displaying that information only. Over time, we could grow the amount information stored in the database and consequently displayed by the dashboard.

## CI using Docker

Actions allows CI to run either inside the VM directly, which is the current state, or inside a container using docker. It seems that it can be advantageous to use Docker instead for reproducibility. If the VM version changes over time, we can keep using the same docker container and therefore keep the same environment. Actions also only provide a couple of different Linux VMs, while with Docker we have the possibility of running a customized image on different distros.

## Using de-duplication in Actions yaml

To de-duplicate information in an Actions yaml file, we should consider using Anchors: https://medium.com/@kinghuang/docker-compose-anchors-aliases-extensions-a1e4105d70bd

## Flaky tests

CI should not run flaky tests and tests should only be added to CI once they are green and not flaky. If flaky tests are detected in the CI environment, they should be removed from CI and an issue should be open to fix the flakiness. 

Some tests might have issues running inside a docker container - these tests should be discussed on a case by case basis.

## Buildx

Buildx is an experimental docker feature that allows us to build and run an image using transparent multi architecture emulation (https://mirailabs.io/blog/multiarch-docker-with-buildx/). Currently Gitlab CI uses chroot+qemu but buildx might be the way to go in the future. 

## OSS-fuzz

Racket was now accepted into the OSS-fuzz project. Next step is to write a fuzzer for both Racket3M and RacketCS. Depending on the available C API on RacketCS this might be trickier than for Racket3M, however doing it for CS is more urgent since sooner or later this will become the default backend. Reference on writing a fuzzer: http://llvm.org/docs/LibFuzzer.html

## Next steps plan

* Simplify build yaml using anchors;
* Add more tests for CGC, 3M and CS;
* Run jobs inside containers;
* Implement fuzzer for oss-fuzz;