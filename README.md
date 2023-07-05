Github-CI:<br>
[![Build Status][github_linux_status]][github_linux_link]
[![Build Status][github_macos_status]][github_macos_link]
[![Build Status][github_windows_status]][github_windows_link]

[![Build Status][github_amd64_docker_status]][github_amd64_docker_link]

[github_linux_status]: ./../../actions/workflows/amd64_linux.yml/badge.svg
[github_linux_link]: ./../../actions/workflows/amd64_linux.yml
[github_macos_status]: ./../../actions/workflows/amd64_macos.yml/badge.svg
[github_macos_link]: ./../../actions/workflows/amd64_macos.yml
[github_windows_status]: ./../../actions/workflows/amd64_windows.yml/badge.svg
[github_windows_link]: ./../../actions/workflows/amd64_windows.yml

[github_amd64_docker_status]: ./../../actions/workflows/amd64_docker.yml/badge.svg
[github_amd64_docker_link]: ./../../actions/workflows/amd64_docker.yml

# Introduction

<nav for="bazel"> |
<a href="#dependencies">Dependencies</a> |
<a href="#build">Build</a> |
<a href="#test">Test</a> |
<a href="ci/README.md">CI</a> |
</nav>

Bazel Template with OR-Tools integration.
If you don't have Bazel installed already, you can download it for free from
<https://bazel.build/>.

# Dependencies
Take a look at the [WORKSPACE](WORKSPACE) file.

# Build
On any *\*NIX* (MacOS, GNU/Linux) platform:
```sh
bazel build --cxxopt=-std=c++20 //main:template
```

On Windows when using *MSVC 2019+*:
```cmd
bazel build --cxxopt="-std:c++20" ///main:template
```

# Test
On any *\*NIX* (MacOS, GNU/Linux) platform:
```sh
bazel test --cxxopt=-std=c++20 //main:template
```

On Windows when using *MSVC 2019+*:
```cmd
bazel test --cxxopt="-std:c++20" ///main:template
```

