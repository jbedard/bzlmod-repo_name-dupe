Repositories should only be loaded once.

Repositories loaded in WORKSPACE should be shadowed by any modules of the same name loaded with `bazel_dep` in MODULE.bazel. The "name" in MODULE should be the `bazel_dep(repo_name)` falling back to `bazel_dep(name)`, the "name" in WORKSPACE should be the `http_archive(name)` (or `git_repository` etc).

This repository shows `bazel_dep(name = "aspect_bazel_lib", version = "2.3.0", repo_name = "foobar")` in MODULE.bazel NOT shadowing the `aspect_bazel_lib` loaded by `rules_js` via `rules_js_dependencies()` in WORKSPACE.
