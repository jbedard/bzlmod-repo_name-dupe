workspace(
    name = "bzlmod-dupes",
)

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# Node setup
http_archive(
    name = "rules_nodejs",
    sha256 = "a50986c7d2f2dc43a5b9b81a6245fd89bdc4866f1d5e316d9cef2782dd859292",
    strip_prefix = "rules_nodejs-6.0.5",
    url = "https://github.com/bazelbuild/rules_nodejs/releases/download/v6.0.5/rules_nodejs-v6.0.5.tar.gz",
)

load("@rules_nodejs//nodejs:repositories.bzl", "nodejs_register_toolchains")

nodejs_register_toolchains(
    name = "nodejs",
    node_version = "19.7.0",
)

# Aspect Node
http_archive(
    name = "aspect_rules_js",
    sha256 = "630a71aba66c4023a5b16ab3efafaeed8b1a2865ccd168a34611eb73876b3fc4",
    strip_prefix = "rules_js-1.37.1",
    url = "https://github.com/aspect-build/rules_js/releases/download/v1.37.1/rules_js-v1.37.1.tar.gz",
)

load("@aspect_rules_js//js:repositories.bzl", "rules_js_dependencies")

rules_js_dependencies()

load("@aspect_rules_js//npm:npm_import.bzl", "npm_translate_lock")

npm_translate_lock(
    name = "npm",
    pnpm_lock = "//:pnpm-lock.yaml",
    pnpm_version = "8.10.2",
    verify_node_modules_ignored = "//:.bazelignore",
)

load("@npm//:repositories.bzl", "npm_repositories")

npm_repositories()
