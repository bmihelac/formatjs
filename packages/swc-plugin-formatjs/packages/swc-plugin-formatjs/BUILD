load("@swc_plugin_formatjs_crate_index//:defs.bzl", "aliases", "all_crate_deps")
load("@rules_rust//rust:defs.bzl", "rust_library", "rust_test")
load(":wasm.bzl", "rust_wasm_library")

package(default_visibility = ["//packages/swc-plugin-formatjs:__subpackages__"])

rust_library(
    name = "swc-plugin-formatjs",
    srcs = glob(["src/**/*.rs"]),
    aliases = aliases(),
    proc_macro_deps = all_crate_deps(
        proc_macro = True,
    ),
    deps = ["//packages/swc-plugin-formatjs/packages/swc-formatjs-visitor"] + all_crate_deps(
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
    crate = ":lib",
    proc_macro_deps = all_crate_deps(
        proc_macro_dev = True,
    ),
    deps = all_crate_deps(
        normal_dev = True,
    ),
    tags = ["manual"],
)

rust_wasm_library(
    name = "swc_plugin_formatjs.wasm",
    srcs = glob(["src/**/*.rs"]),
    aliases = aliases(),
    proc_macro_deps = all_crate_deps(
        proc_macro = True,
    ),
    wasi = True,
    deps = ["//packages/swc-plugin-formatjs/packages/swc-formatjs-visitor"] + all_crate_deps(
        normal = True,
    ),
    tags = ["manual"],
)
