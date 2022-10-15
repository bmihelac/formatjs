load("@aspect_rules_js//npm/private:npm_package.bzl", "npm_package")
load("@aspect_bazel_lib//lib:copy_file.bzl", "copy_file")
load("//tools:jest.bzl", "jest_test")

# npm_link_all_packages(name = "node_modules")

PACKAGE_NAME = "swc-plugin-formatjs"

copy_file(
    name = "wasm",
    src = "//packages/swc-plugin-formatjs/packages/swc-plugin-formatjs:swc_plugin_formatjs.wasm",
    out = "swc_plugin_formatjs.wasm",
    tags = ["manual"],
)

npm_package(
    name = PACKAGE_NAME,
    srcs = [
        "LICENSE.md",
        "README.md",
        "package.json",
        ":wasm",
    ],
    package = "@formatjs/%s" % PACKAGE_NAME,
    visibility = ["//visibility:public"],
    tags = ["manual"],
)

jest_test(
    name = "test_plugin",
    srcs = glob(
        ["spec/**/*.spec.ts"],
    ),
    jest_config = "jest.config.js",
    snapshots = glob([
        "tests/**/*.snap",
    ]),
    deps = [
        "spec/transform.ts",
        ":wasm",
        "//:node_modules/@swc/core",
        "//:node_modules/@swc/jest",
    ] + glob([
        "spec/fixtures/**/*",
    ]),
    tags = ["manual"],
)
