load("@rules_proto//proto:defs.bzl", "proto_library")
load("@io_bazel_rules_go//go:def.bzl", "go_library")
load("@io_bazel_rules_go//proto:def.bzl", "go_proto_library")
load("@rules_cc//cc:defs.bzl", "cc_proto_library")
load("@com_github_grpc_grpc//bazel:cc_grpc_library.bzl", "cc_grpc_library")

proto_library(
    name = "tester_proto",
    srcs = ["tester.proto"],
    visibility = ["//visibility:public"],
    deps = ["@com_google_protobuf//:timestamp_proto"],
)

cc_proto_library(
    name = "tester_cc_proto",
    visibility = ["//visibility:public"],
    deps = [":tester_proto"],
)

cc_grpc_library(
    name = "tester_cc_grpc",
    srcs = [":tester_proto"],
    grpc_only = True,
    visibility = ["//visibility:public"],
    deps = [":tester_cc_proto"],
)

go_proto_library(
    name = "tester_go_proto",
    importpath = "collective/nanoprobes/v0/tester",
    proto = ":tester_proto",
    visibility = ["//visibility:public"],
)

go_library(
    name = "tester",
    embed = [":tester_go_proto"],
    importpath = "collective/nanoprobes/v0/tester",
    visibility = ["//visibility:public"],
)
