# Introduction
Bazel Template with OR-Tools integration

# Dependencies
Take a look at the [WORKSPACE](WORKSPACE) file.

# Build
On any *\*NIX* (MacOS, GNU/Linux) platform:
```sh
bazel build --cxxopt=-std=c++17 //main:template
```

On Windows when using *MSVC 2019+*:
```cmd
bazel build --cxxopt="-std:c++17" ///main:template
```
