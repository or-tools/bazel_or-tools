Github-CI:<br>
[![Build Status][github_amd64_linux_status]][github_amd64_linux_link]
[![Build Status][github_amd64_macos_status]][github_amd64_macos_link]
[![Build Status][github_amd64_windows_status]][github_amd64_windows_link]  
[![Build Status][github_arm64_macos_status]][github_arm64_macos_link]

[![Build Status][github_amd64_docker_status]][github_amd64_docker_link]

[github_amd64_linux_status]: ./../../actions/workflows/amd64_linux.yml/badge.svg
[github_amd64_linux_link]: ./../../actions/workflows/amd64_linux.yml
[github_amd64_macos_status]: ./../../actions/workflows/amd64_macos.yml/badge.svg
[github_amd64_macos_link]: ./../../actions/workflows/amd64_macos.yml
[github_amd64_windows_status]: ./../../actions/workflows/amd64_windows.yml/badge.svg
[github_amd64_windows_link]: ./../../actions/workflows/amd64_windows.yml

[github_arm64_macos_status]: ./../../actions/workflows/arm64_macos.yml/badge.svg
[github_arm64_macos_link]: ./../../actions/workflows/arm64_macos.yml

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
Take a look at the [MODULE.bazel](MODULE.bazel) file.

# Build

To build the C++ project, as usual:
```sh
bazel build -c opt :all
```

# Test

To test the C++ project, as usual:

```sh
bazel test -c opt --test_output=all :all
```

