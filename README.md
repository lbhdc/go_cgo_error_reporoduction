# reproduction
Running `govulncheck` in the root of this reposiotry will cause go to fail complaining of c++ sources.
```shell
$ govulncheck ./...
govulncheck is an experimental tool. Share feedback at https://go.dev/s/govulncheck-feedback.

Scanning for dependencies with known vulnerabilities...
govulncheck: Packages contain errors:
-: C++ source files not allowed when not using cgo or SWIG: tester.grpc.pb.cc tester.pb.cc
```

If the go code is not relying on cgo, then disabling cgo doesn't cause the go toolchain to error.
```shell
CGO_ENABLED=0 govulncheck ./...
govulncheck is an experimental tool. Share feedback at https://go.dev/s/govulncheck-feedback.

Scanning for dependencies with known vulnerabilities...
No vulnerabilities found.
```
