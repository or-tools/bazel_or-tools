load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

git_repository(
    name = "bazel_skylib",
    commit = "2ec2e6d",  # release 1.0.3
    remote = "https://github.com/bazelbuild/bazel-skylib.git",
)

http_archive(
    name = "zlib",
    build_file = "@com_google_protobuf//:third_party/zlib.BUILD",
    sha256 = "c3e5e9fdd5004dcb542feda5ee4f0ff0744628baf8ed2dd5d66f8ca1197cb1a1",
    strip_prefix = "zlib-1.2.11",
    urls = [
        "https://mirror.bazel.build/zlib.net/zlib-1.2.11.tar.gz",
        "https://zlib.net/zlib-1.2.11.tar.gz",
    ],
)

git_repository(
    name = "com_google_absl",
    commit = "0f3bb46", # release 20200923.2
    remote = "https://github.com/abseil/abseil-cpp.git",
)

git_repository(
    name = "rules_python",
    commit = "c8c79aa", #0.1.0
    remote = "https://github.com/bazelbuild/rules_python.git",
)

git_repository(
    name = "com_google_protobuf",
    commit = "2514f0b",  # release v3.14.0
    remote = "https://github.com/protocolbuffers/protobuf.git",
)
#load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")

git_repository(
    name = "com_google_ortools",
    commit = "b77bd3a", # release v8.1
    remote = "https://github.com/google/or-tools.git",
)

http_archive(
    name = "bliss",
    build_file = "@com_google_ortools//bazel:bliss.BUILD",
    patches = ["@com_google_ortools//bazel:bliss-0.73.patch"],
    sha256 = "f57bf32804140cad58b1240b804e0dbd68f7e6bf67eba8e0c0fa3a62fd7f0f84",
    url = "http://www.tcs.hut.fi/Software/bliss/bliss-0.73.zip",
)

http_archive(
    name = "scip",
    build_file = "@com_google_ortools//bazel:scip.BUILD",
    patches = ["@com_google_ortools//bazel:scip.patch"],
    sha256 = "033bf240298d3a1c92e8ddb7b452190e0af15df2dad7d24d0572f10ae8eec5aa",
    url = "https://github.com/google/or-tools/releases/download/v7.7/scip-7.0.1.tgz",
)

