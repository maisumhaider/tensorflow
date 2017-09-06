# Description:
# ARM's Compute Library

licenses(["notice"]) # MIT

exports_files(["LICENSE"])

cc_library(
    name = "acl",
    visibility = ["//visibility:public"],
    includes = ["include", "arm_compute", "."],
    deps = ["@acl_archive//:acl_headers"],
)
