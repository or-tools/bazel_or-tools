[![Status][linux_svg]][linux_link]

[linux_svg]: https://github.com/or-tools/bazel_or-tools/workflows/Docker/badge.svg?branch=main
[linux_link]: https://github.com/or-tools/bazel_or-tools/actions?query=workflow%3A"Docker"

# Introduction
<nav for="bazel"> |
<a href="#deps">Dependencies</a> |
<a href="#build">Build</a> |
<a href="ci/README.md">CI</a> |
</nav>

Bazel Template with OR-Tools integration.
If you don't have Bazel installed already, you can download it for free from
<https://bazel.build/>.

<a name="deps"></a>
# Dependencies
Take a look at the [WORKSPACE](WORKSPACE) file.

<a name="build"></a>
# Build
On any *\*NIX* (MacOS, GNU/Linux) platform:
```sh
bazel build --cxxopt=-std=c++17 //main:template
```

On Windows when using *MSVC 2019+*:
```cmd
bazel build --cxxopt="-std:c++17" ///main:template
```
