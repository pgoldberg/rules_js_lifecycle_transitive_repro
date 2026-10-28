# rules_js bug repro: missing runfiles for an npm_package that depends on a package with a lifecycle hook

```
$ bazel test //:test --test_output=errors
Error: Cannot find module 'has-flag'
//:test    FAILED
```

`has-flag` is a dependency of `supports-color`, which is a dependency of `chalk`. With `allowBuilds: {}` in the `pnpm-workspace.yaml`, the test passes.
