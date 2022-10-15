load("@swc_plugin_formatjs_crate_index//:defs.bzl", "aliases", "all_crate_deps")
load("@rules_rust//rust:defs.bzl", "rust_library", "rust_test")

rust_library(
    name = "swc-formatjs-visitor",
    srcs = glob(["src/**/*.rs"]),
    aliases = aliases(),
    proc_macro_deps = all_crate_deps(
        proc_macro = True,
    ),
    visibility = ["//packages/swc-plugin-formatjs:__subpackages__"],
    deps = ["//packages/swc-plugin-formatjs/packages/icu-messageformat-parser"] + all_crate_deps(
        normal = True,
    ),
    tags = ["manual"],
)

rust_test(
    name = "unit_test",
    aliases = aliases(
        normal_dev = True,
        proc_macro_dev = True,
    ),
    crate = ":swc-formatjs-visitor",
    proc_macro_deps = all_crate_deps(
        proc_macro_dev = True,
    ),
    deps = all_crate_deps(
        normal_dev = True,
    ),
    tags = ["manual"],
)
