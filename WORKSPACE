workspace(name = "org_ortools_template")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository", "new_git_repository")

# Bazel Extensions
## Bazel Skylib rules.
git_repository(
    name = "bazel_skylib",
    tag = "1.4.1",
    remote = "https://github.com/bazelbuild/bazel-skylib.git",
)
load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")
bazel_skylib_workspace()

## Bazel rules.
git_repository(
    name = "platforms",
    tag = "0.0.6",
    remote = "https://github.com/bazelbuild/platforms.git",
)

git_repository(
    name = "rules_cc",
    tag = "0.0.6",
    remote = "https://github.com/bazelbuild/rules_cc.git",
)

git_repository(
    name = "rules_proto",
    tag = "5.3.0-21.7",
    remote = "https://github.com/bazelbuild/rules_proto.git",
)

git_repository(
    name = "rules_jvm_external",
    tag = "5.2",
    #tag = "5.3",
    remote = "https://github.com/bazelbuild/rules_jvm_external.git",
)

git_repository(
    name = "contrib_rules_jvm",
    tag = "v0.9.0",
    #tag = "v0.14.0",
    remote = "https://github.com/bazel-contrib/rules_jvm.git",
)

git_repository(
    name = "rules_python",
    tag = "0.23.1",
    remote = "https://github.com/bazelbuild/rules_python.git",
)

# Dependencies
## ZLIB
new_git_repository(
    name = "zlib",
    build_file = "@com_google_protobuf//:third_party/zlib.BUILD",
    tag = "v1.2.13",
    remote = "https://github.com/madler/zlib.git",
)

## Re2
git_repository(
    name = "com_google_re2",
    tag = "2023-07-01",
    remote = "https://github.com/google/re2.git",
)

## Abseil-cpp
git_repository(
    name = "com_google_absl",
    tag = "20230125.3",
    patches = ["//patches:abseil-cpp-20230125.3.patch"],
    patch_args = ["-p1"],
    remote = "https://github.com/abseil/abseil-cpp.git",
)

## Protobuf
git_repository(
    name = "com_google_protobuf",
    tag = "v23.3",
    patches = ["//patches:protobuf-v23.3.patch"],
    patch_args = ["-p1"],
    remote = "https://github.com/protocolbuffers/protobuf.git",
)
# Load common dependencies.
load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")
protobuf_deps()

## Solvers
http_archive(
    name = "glpk",
    build_file = "//bazel:glpk.BUILD",
    sha256 = "4a1013eebb50f728fc601bdd833b0b2870333c3b3e5a816eeba921d95bec6f15",
    url = "http://ftp.gnu.org/gnu/glpk/glpk-5.0.tar.gz",
)

http_archive(
    name = "bliss",
    build_file = "@com_google_ortools//bazel:bliss.BUILD",
    patches = ["@com_google_ortools//bazel:bliss-0.73.patch"],
    sha256 = "f57bf32804140cad58b1240b804e0dbd68f7e6bf67eba8e0c0fa3a62fd7f0f84",
    url = "http://www.tcs.hut.fi/Software/bliss/bliss-0.73.zip",
)

new_git_repository(
    name = "scip",
    build_file = "@com_google_ortools//bazel:scip.BUILD",
    patches = ["@com_google_ortools//bazel:scip.patch"],
    patch_args = ["-p1"],
    tag = "v800",
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
    name = 'eigen3',
    srcs = [],
    includes = ['.'],
    hdrs = glob(['Eigen/**']),
    visibility = ['//visibility:public'],
)
""")

## Testing
git_repository(
    name = "com_google_googletest",
    tag = "v1.13.0",
    remote = "https://github.com/google/googletest.git",
)

git_repository(
    name = "com_google_benchmark",
    tag = "v1.8.1",
    remote = "https://github.com/google/benchmark.git",
)


git_repository(
    name = "com_google_ortools",
    branch = "main",
    #tag = "v9.6",
    remote = "https://github.com/google/or-tools.git",
)
