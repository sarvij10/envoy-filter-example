package(default_visibility = ["//visibility:public"])

load(
    "@envoy//bazel:envoy_build_system.bzl",
    "envoy_cc_binary",
    "envoy_cc_library",
    "envoy_cc_test",
)

load("@envoy_api//bazel:api_build_system.bzl", "api_proto_package")

envoy_cc_binary(
    name = "envoy",
    repository = "@envoy",
    deps = [
        ":modify_buffer_config",
        "@envoy//source/exe:envoy_main_entry_lib",
    ],
)

api_proto_package()

envoy_cc_library(
    name = "empty_http_filter_config_lib",
    hdrs = ["empty_http_filter_config.h"],
    repository = "@envoy",
    deps = [
        "@envoy//include/envoy/server:filter_config_interface",
    ],
)

envoy_cc_library(
    name = "modify_buffer_config",
    srcs = ["modify_buffer_filter.cc"],
    repository = "@envoy",
    deps = [
        ":empty_http_filter_config_lib",
        "@envoy//source/exe:envoy_common_lib",
        "@envoy//include/envoy/http:filter_interface",
        "@envoy//include/envoy/registry",
        "@envoy//include/envoy/server:filter_config_interface",
        "@envoy//source/extensions/filters/http/common:pass_through_filter_lib",
    ],
)

envoy_cc_library(
        name = "modify_buffer_filter",
        repository = "@envoy",
        deps = [ ":modify_buffer_config",],
)
