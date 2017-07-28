# Description:
# ARM's Compute Library

licenses(["LICENSE"]) # MIT

cc_library(
    name = "arm_compute_library",
    srcs = glob([
        "./utils/Utils.cpp",
        "./src/**",
    ]),
    hdrs = glob([
        "./include/**",
        "./utils/Utils.h",
        "./arm_compute/**",
        "./src/**",
    ]),
    copts = [
    ]
    includes = ["include"],
)
