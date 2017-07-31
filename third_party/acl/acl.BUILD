genrule(
    name = "generate_fake_compute_version",
    outs = [":arm_compute_version.embed"],
    cmd = 'echo "\\"arm_compute_version=v17.06 Build options: {\'arch\': \'x86_64\', \'opencl\': \'0\', \'neon\': \'0\', \'debug\': \'1\', \'os\': \'linux\', \'Werror\': \'1\'} Git hash=db0e610fa90a4c7c534049792ee7fe143d46f72f\\" " > $@',
)

cc_library(
    name = "libarm_compute_objects",
    hdrs = [":arm_compute_version.embed"],
    srcs = glob(["include/*.cpp", "src/**/*.cpp"]),
    includes = ["include", "arm_compute", "."],
    copts = ["-Wno-deprecated-declarations",
             "-Wall", "-DARCH_ARM", "-Wextra", "-Wno-unused-parameter",
             "-pedantic", "-Wdisabled-optimization", "-Wformat=2", "-Winit-self",
             "-Wstrict-overflow=2", "-Wswitch-default", "-fpermissive",
             "-std=gnu++11", "-Wno-vla", "-Woverloaded-virtual", "-Wctor-dtor-privacy",
             "-Wsign-promo", "-Weffc++", "-Wno-format-nonliteral", "-Wno-overlength-strings",
             "-Wno-strict-overflow", "-Wlogical-op", "-Wnoexcept", "-Wstrict-null-sentinel",
             "-Wno-ignored-attributes", "-Werror", "-O0", "-g", "-gdwarf-2", "-m64",
             "-D_GLIBCXX_USE_NANOSLEEP", "-DARM_COMPUTE_CPP_SCHEDULER=1",
             "-DARM_COMPUTE_DEBUG_ENABLED",  "-DARM_COMPUTE_ASSERTS_ENABLED"],
    visibility = ["//visibility:public"],
    linkstatic=1,
)

cc_binary(
    name = "libacl.so",
    linkopts = [
        "-lpthread",
        "-ldl",
        "-m64",
    ],
    linkshared = 1,
    deps = [
        ":libarm_compute_objects",
    ],
    visibility = ["//visibility:public"],
)
