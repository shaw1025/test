load("//transpiler:fhe.bzl", "fhe_cc_library")
load("@bazel_skylib//:bzl_library.bzl", "bzl_library")

licenses(["notice"])

fhe_cc_library(
    name = "sqrt_tfhe",
    src = "sqrt.cc",
    hdrs = ["sqrt.h"],
    num_opt_passes = 2,
)

fhe_cc_library(
    name = "sqrt_yosys_plaintext",
    src = "sqrt.cc",
    hdrs = ["sqrt.h"],
    transpiler_type = "yosys_plaintext",
)

fhe_cc_library(
    name = "sqrt_yosys_interpreted_tfhe",
    src = "sqrt.cc",
    hdrs = ["sqrt.h"],
    transpiler_type = "yosys_interpreted_tfhe",
)

fhe_cc_library(
    name = "sqrt_interpreted_tfhe",
    src = "sqrt.cc",
    hdrs = ["sqrt.h"],
    num_opt_passes = 2,
    transpiler_type = "interpreted_tfhe",
)

fhe_cc_library(
    name = "sqrt_palisade",
    src = "sqrt.cc",
    hdrs = ["sqrt.h"],
    num_opt_passes = 2,
    transpiler_type = "palisade",
)

fhe_cc_library(
    name = "sqrt_interpreted_palisade",
    src = "sqrt.cc",
    hdrs = ["sqrt.h"],
    num_opt_passes = 2,
    transpiler_type = "interpreted_palisade",
)

fhe_cc_library(
    name = "sqrt_bool",
    src = "sqrt.cc",
    hdrs = ["sqrt.h"],
    num_opt_passes = 2,
    transpiler_type = "bool",
)

cc_binary(
    name = "sqrt_tfhe_testbench",
    srcs = [
        "sqrt_tfhe_testbench.cc",
    ],
    deps = [
        ":sqrt_tfhe",
        "//transpiler/data:tfhe_data",
        "@com_google_absl//absl/base",
        "@com_google_absl//absl/strings",
        "@com_google_xls//xls/common/logging",
        "@com_google_xls//xls/common/status:status_macros",
        "@tfhe//:libtfhe",
    ],
)

cc_binary(
    name = "sqrt_interpreted_tfhe_testbench",
    srcs = [
        "sqrt_tfhe_testbench.cc",
    ],
    copts = ["-DUSE_INTERPRETED_TFHE"],
    deps = [
        ":sqrt_interpreted_tfhe",
        "//transpiler/data:tfhe_data",
        "@com_google_absl//absl/base",
        "@com_google_absl//absl/strings",
        "@com_google_xls//xls/common/logging",
        "@com_google_xls//xls/common/status:status_macros",
        "@tfhe//:libtfhe",
    ],
)

cc_binary(
    name = "sqrt_yosys_interpreted_tfhe_testbench",
    srcs = [
        "sqrt_tfhe_testbench.cc",
    ],
    copts = ["-DUSE_YOSYS_INTERPRETED_TFHE"],
    deps = [
        ":sqrt_yosys_interpreted_tfhe",
        "//transpiler/data:tfhe_data",
        "@com_google_absl//absl/base",
        "@com_google_absl//absl/strings",
        "@com_google_xls//xls/common/logging",
        "@com_google_xls//xls/common/status:status_macros",
        "@tfhe//:libtfhe",
    ],
)

cc_binary(
    name = "sqrt_palisade_testbench",
    srcs = [
        "sqrt_palisade_testbench.cc",
    ],
    deps = [
        ":sqrt_palisade",
        "//transpiler/data:palisade_data",
        "@com_google_absl//absl/base",
        "@com_google_absl//absl/strings",
        "@com_google_xls//xls/common/logging",
        "@com_google_xls//xls/common/status:status_macros",
        "@palisade//:binfhe",
    ],
)

cc_binary(
    name = "sqrt_interpreted_palisade_testbench",
    srcs = [
        "sqrt_palisade_testbench.cc",
    ],
    copts = ["-DUSE_INTERPRETED_PALISADE"],
    deps = [
        ":sqrt_interpreted_palisade",
        "//transpiler/data:palisade_data",
        "@com_google_absl//absl/base",
        "@com_google_absl//absl/strings",
        "@com_google_xls//xls/common/logging",
        "@com_google_xls//xls/common/status:status_macros",
        "@palisade//:binfhe",
    ],
)

cc_binary(
    name = "sqrt_bool_testbench",
    srcs = [
        "sqrt_bool_testbench.cc",
    ],
    deps = [
        ":sqrt_bool",
        "//transpiler/data:boolean_data",
        "@com_google_absl//absl/container:fixed_array",
        "@com_google_absl//absl/strings",
        "@com_google_xls//xls/common/logging",
        "@com_google_xls//xls/common/status:status_macros",
    ],
)

cc_binary(
    name = "sqrt_yosys_plaintext_testbench",
    srcs = [
        "sqrt_bool_testbench.cc",
    ],
    copts = ["-DUSE_YOSYS_PLAINTEXT"],
    deps = [
        ":sqrt_yosys_plaintext",
        "//transpiler/data:boolean_data",
        "@com_google_absl//absl/container:fixed_array",
        "@com_google_absl//absl/strings",
        "@com_google_xls//xls/common/logging",
        "@com_google_xls//xls/common/status:status_macros",
    ],
)

cc_library(
    name = "sqrt",
    srcs = ["sqrt.cc"],
    hdrs = ["sqrt.h"],
)

cc_test(
    name = "sqrt_test",
    size = "large",
    srcs = ["sqrt_test.cc"],
    shard_count = 8,
    deps = [
        ":sqrt",
        ":sqrt_tfhe",
        "//transpiler/data:tfhe_data",
        "@com_google_absl//absl/base",
        "@com_google_googletest//:gtest_main",
        "@com_google_xls//xls/common/status:matchers",
        "@tfhe//:libtfhe",
    ],
)