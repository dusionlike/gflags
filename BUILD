# Bazel (http://bazel.io/) BUILD file for gflags.
#
# See INSTALL.md for instructions for adding gflags to a Bazel workspace.

licenses(["notice"])

exports_files(["src/gflags_completions.sh", "COPYING.txt"])

alias(
    name = "windows",
    actual = select({
        ":windows_x64": ":windows_x64",
        ":windows_x86": ":windows_x86",
        "//conditions:default": ":windows_x64",
    }),
    visibility = ["//visibility:public"],
)

config_setting(
    name = "windows_x64",
    values = {"cpu": "x64_windows"},
)

config_setting(
    name = "windows_x86",
    values = {"cpu": "x64_x86_windows"},
)

load(":bazel/gflags.bzl", "gflags_sources", "gflags_library")

(hdrs, srcs) = gflags_sources(namespace=["gflags", "google"])
gflags_library(hdrs=hdrs, srcs=srcs, threads=0)
gflags_library(hdrs=hdrs, srcs=srcs, threads=1)
