[![Status][linux_svg]][linux_link]
[![Status][macos_svg]][macos_link]
[![Status][windows_svg]][windows_link]
[![Status][docker_svg]][docker_link]

[linux_svg]: https://github.com/or-tools/bazel_or-tools/actions/workflows/linux.yml/badge.svg
[linux_link]: https://github.com/or-tools/bazel_or-tools/actions/workflows/linux.yml
[macos_svg]: https://github.com/or-tools/bazel_or-tools/actions/workflows/macos.yml/badge.svg
[macos_link]: https://github.com/or-tools/bazel_or-tools/actions/workflows/macos.yml
[windows_svg]: https://github.com/or-tools/bazel_or-tools/actions/workflows/windows.yml/badge.svg
[windows_link]: https://github.com/or-tools/bazel_or-tools/actions/workflows/windows.yml
[docker_svg]: https://github.com/or-tools/bazel_or-tools/actions/workflows/docker.yml/badge.svg
[docker_link]: https://github.com/or-tools/bazel_or-tools/actions/workflows/docker.yml

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

