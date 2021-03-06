# CI: Makefile/Docker testing
To test the build on various distro, I'm using docker containers and a Makefile for orchestration.

pros:
* You are independent of third party CI runner config (e.g. github actions runners or Travis-CI VM images).
* You can run it locally on your linux system.
* Most CI provide runner with docker and Makefile installed (e.g. tarvis-ci [minimal images](https://docs.travis-ci.com/user/languages/minimal-and-generic/).

cons:
* Only GNU/Linux distro supported.
* Could take ~3.5GiB for each distro
  * ~1GiB OS + C++/CMake tools
  * ~2GiB bazel build

# Usage
To get the help simply type:
```sh
make
```

note: you can also use from top directory
```sh
make --directory=ci
```

## Example
For example to test inside an `Ubuntu` container:
```sh
make ubuntu_test
```

# Docker Layers
Dockerfile is splitted in several stages.

![docker](doc/docker.svg)
