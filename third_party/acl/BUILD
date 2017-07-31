# Description:
# ARM's Compute Library

licenses(["notice"]) # MIT

exports_files(["LICENSE"])

cc_library(
    name = "acl",
    visibility = ["//visibility:public"],
    includes = ["."],
    srcs = ["@acl_archive//:libacl.so"],
)
