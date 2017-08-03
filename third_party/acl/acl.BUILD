genrule(
    name = "generate_fake_compute_version",
    outs = [":arm_compute_version.embed"],
    cmd = 'echo "\\"arm_compute_version=v17.06 Build options: {\'arch\': \'armv7a\', \'opencl\': \'1\', \'neon\': \'1\', \'debug\': \'0\', \'os\': \'linux\', \'Werror\': \'0\'} Git hash=db0e610fa90a4c7c534049792ee7fe143d46f72f\\" " > $@'
)

cc_library(
    name = "libarm_compute_objects",
    hdrs = [":arm_compute_version.embed"],
    srcs = glob(["include/*.cpp", "src/**/*.cpp", "arm_compute/**/*.cpp"]),
    includes = ["include", "arm_compute", "."],
    copts = ["-Wno-deprecated-declarations",
             "-Wall", "-DARCH_ARM", "-Wextra", "-Wno-unused-parameter",
             "-pedantic", "-Wdisabled-optimization", "-Wformat=2", "-Winit-self",
             "-Wstrict-overflow=2", "-Wswitch-default", "-fpermissive",
             "-std=gnu++11", "-Wno-vla", "-Woverloaded-virtual", "-Wctor-dtor-privacy",
             "-Wsign-promo", "-Weffc++", "-Wno-format-nonliteral", "-Wno-overlength-strings",
             "-Wno-strict-overflow", "-Wlogical-op", "-Wnoexcept", "-Wstrict-null-sentinel",
             "-Wno-ignored-attributes", "-march=armv7-a", "-mthumb", "-mfpu=neon", "-mfloat-abi=hard", "-O3", "-ftree-vectorize",
             "-D_GLIBCXX_USE_NANOSLEEP", "-DARM_COMPUTE_CPP_SCHEDULER=1", "-fPIC",
             "-DARM_COMPUTE_DEBUG_ENABLED",  "-DARM_COMPUTE_ASSERTS_ENABLED"],
    visibility = ["//visibility:public"],
    linkstatic=1,
)

cc_binary(
    name = "libacl.so",
    linkopts = [
        "-lpthread",
        "-ldl",
        "-fopenmp",
    ],
    linkshared = 1,
    deps = [
        ":libarm_compute_objects",
    ],
    visibility = ["//visibility:public"],
)

cc_library(
    name = "acl_headers",
    srcs = glob(["**/*.h"]),
    includes = [".", "include", "arm_compute"],
    visibility = ["//visibility:public"],
)
