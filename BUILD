package(default_visibility = ["//visibility:public"])
licenses(["notice"])

AM_CXXFLAGS = [
    "-Wall",
    "-Wwrite-strings",
    "-Woverloaded-virtual",
    "-Wno-sign-compare",
    "-fno-builtin-malloc",
    "-fno-builtin-free",
    "-fno-builtin-realloc",
    "-fno-builtin-calloc",
    "-fno-builtin-cfree",
    "-fno-builtin-memalign",
    "-fno-builtin-posix_memalign",
    "-fno-builtin-valloc",
    "-fno-builtin-pvalloc",
    "-fno-builtin",
    "-std=c++17",
]
#genrule(
#    name = "gperftools-configure",
#    srcs = glob(["**/*"]),
#    outs = [
#        "src/config.h",
#        "src/gperftools/tcmalloc.h",
#    ],
#    cmd = ""
#    #+ "gperf=\"external/gperftools\"; "
#    + "outs=($(OUTS)); "
#    #+ "cp -r $${gperf} build/; "
#    + "( cd build;  ./configure; ); "
#    + "cp build/src/config.h              \"$${outs[0]}\"; "
#    + "cp build/src/gperftools/tcmalloc.h \"$${outs[1]}\"; "
#    ,
#    #cmd = "./configure;"
#    #+ "cp /src/config.h              \"$${outs[0]}\"; "
#    #+ "cp /src/gperftools/tcmalloc.h \"$${outs[1]}\"; "
#)
cc_library(
    name = "gperftools",
    hdrs = [
        "src/gperftools/heap-checker.h",
        "src/gperftools/heap-profiler.h",
        "src/gperftools/malloc_extension.h",
        "src/gperftools/malloc_extension_c.h",
        "src/gperftools/malloc_hook.h",
        "src/gperftools/malloc_hook_c.h",
        "src/gperftools/profiler.h",
        "src/gperftools/stacktrace.h",
        "src/gperftools/tcmalloc.h",
        "src/gperftools/nallocx.h",
	"src/tcmalloc.cc",
    ],
    srcs = glob([
            "src/*.cc",
            "src/*.h",
            "src/base/*.cc",
            "src/base/*.h",
        ],
        exclude = [
            "src/debugallocation.cc",
        ],
    )+ [
       # ":gperftools-configure"
    ],
    includes = [ "src/",],
	#	"src/base/",
	#	"src/gperftoos/"],
    copts = AM_CXXFLAGS,
)
