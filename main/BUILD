load("@rules_cc//cc:defs.bzl", "cc_binary", "cc_test")

cc_binary(
    name = "template",
    srcs = ["template.cc"],
    deps = [
        "@com_google_ortools//ortools/base",
        "@com_google_ortools//ortools/linear_solver",
        "@com_google_ortools//ortools/linear_solver:linear_solver_cc_proto",
    ],
)

cc_test(
    name = "test_template",
    srcs = ["template.cc"],
    deps = [
        ":template",
        "@com_google_ortools//ortools/base",
        "@com_google_ortools//ortools/linear_solver",
        "@com_google_ortools//ortools/linear_solver:linear_solver_cc_proto",
    ],
)

