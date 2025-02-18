workspace(name = "ortools_template")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository", "new_git_repository")

# Bazel Extensions
## Bazel Skylib rules.
git_repository(
  name = "bazel_skylib",
  tag = "1.7.1",
  remote = "https://github.com/bazelbuild/bazel-skylib.git",
)
load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")
bazel_skylib_workspace()

## Bazel rules.
git_repository(
  name = "platforms",
  tag = "0.0.10",
  remote = "https://github.com/bazelbuild/platforms.git",
)

git_repository(
  name = "rules_cc",
  tag = "0.1.1",
  remote = "https://github.com/bazelbuild/rules_cc.git",
)

git_repository(
  name = "rules_proto",
  tag = "7.1.0",
  remote = "https://github.com/bazelbuild/rules_proto.git",
)

git_repository(
  name = "io_bazel_rules_go",
  tag = "v0.53.0",
  remote = "https://github.com/bazelbuild/rules_go.git",
)
load("@io_bazel_rules_go//go:deps.bzl", "go_register_toolchains", "go_rules_dependencies")
go_rules_dependencies()
go_register_toolchains(version = "1.24.0")

git_repository(
  name = "rules_java",
  tag = "8.6.3",
  remote = "https://github.com/bazelbuild/rules_java.git",
)

git_repository(
  name = "rules_python",
  tag = "1.0.0",
  remote = "https://github.com/bazelbuild/rules_python.git",
)

load("@rules_python//python:repositories.bzl", "py_repositories")
py_repositories()

# Dependencies

## Abseil-cpp
git_repository(
  name = "com_google_absl",
  tag = "20240722.1",
  remote = "https://github.com/abseil/abseil-cpp.git",
)

## Protobuf
# proto_library, cc_proto_library, and java_proto_library rules implicitly
# depend on @com_google_protobuf for protoc and proto runtimes.
# This statement defines the @com_google_protobuf repo.
git_repository(
  name = "com_google_protobuf",
  tag = "v29.3",
  remote = "https://github.com/protocolbuffers/protobuf.git",
)
# Load common dependencies.
load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")
protobuf_deps()

load("@com_google_protobuf//bazel:system_python.bzl", "system_python")
system_python(
    name = "system_python",
    minimum_python_version = "3.8",
)

http_archive(
    name = "bliss",
    build_file = "//bazel:bliss.BUILD.bazel",
    patches = ["//bazel:bliss-0.73.patch"],
    sha256 = "f57bf32804140cad58b1240b804e0dbd68f7e6bf67eba8e0c0fa3a62fd7f0f84",
    url = "https://github.com/google/or-tools/releases/download/v9.0/bliss-0.73.zip",
    strip_prefix = "bliss-0.73",
    #url = "http://www.tcs.hut.fi/Software/bliss/bliss-0.73.zip",
)

new_git_repository(
    name = "scip",
    build_file = "//bazel:scip.BUILD.bazel",
    patches = ["//bazel:scip-v920.patch"],
    patch_args = ["-p1"],
    tag = "v920",
    remote = "https://github.com/scipopt/scip.git",
)

# Eigen has no Bazel build.
new_git_repository(
    name = "eigen",
    tag = "3.4.0",
    remote = "https://gitlab.com/libeigen/eigen.git",
    build_file_content =
"""
cc_library(
    name = 'eigen',
    srcs = [],
    includes = ['.'],
    hdrs = glob([
      'Eigen/**',
      'unsupported/**',
    ]),
    defines = ["EIGEN_MPL2_ONLY",],
    visibility = ['//visibility:public'],
)
"""
)

git_repository(
  name = "com_google_ortools",
  tag = "v9.12",
  remote = "https://github.com/google/or-tools.git",
)

## Testing
git_repository(
  name = "com_google_googletest",
  tag = "v1.15.2",
  remote = "https://github.com/google/googletest.git",
)

git_repository(
  name = "com_google_benchmark",
  tag = "v1.8.5",
  remote = "https://github.com/google/benchmark.git",
)
