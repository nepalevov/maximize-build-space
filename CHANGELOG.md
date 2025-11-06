# Changelog

## [1.0.0](https://github.com/nepalevov/maximize-build-space/compare/v1.1.0...v1.0.0) (2025-11-06)


### Features

* release 1.0.0 ([dcb7255](https://github.com/nepalevov/maximize-build-space/commit/dcb725594089d071a3ae20a5035e8c774cbd6c18))

## [1.1.0](https://github.com/nepalevov/maximize-build-space/compare/maximize-build-space-v1.0.0...maximize-build-space-v1.1.0) (2025-11-06)

### Features

* initial release 1.0.0 ([581a56f](https://github.com/nepalevov/maximize-build-space/commit/581a56fde419accccf153bda09a5c2482c1f67f2))

* Enforce megabytes in `df` command output if `verbose` is set - more precise for results comparison
* New `set-tmpdir` option to set TMPDIR environment variable to `/mnt` for ephemeral disk storage usage
* New `remove-java` option to remove Java JDK (Temurin), Ant, Gradle and Maven
* New `remove-swift` option to remove Swift toolchain
* New `remove-julia` option to remove Julia
* New `remove-browsers` option to remove Firefox, Chromium, Chrome and Edge (browsers and webdrivers)
* New `remove-cloud-tools` option to remove AWS CLI, Azure CLI, and Google Cloud CLI (keeps GitHub CLI)
* New `remove-kubernetes-tools` option to remove kubectl, helm, kind, minikube and kustomize
* New `remove-powershell` option to remove PowerShell and PowerShell modules (Az modules, etc.)
* New `remove-container-tools` option to remove podman, buildah, skopeo and containernetworking-plugins
* New `remove-rust` option to remove Rust, rustup and cargo
* New `remove-python` option to remove pipx and miniconda
* New `remove-node` option to remove Node.js
* New `remove-go` option to remove Go language
* New `remove-ruby` option to remove Ruby language
* Renamed `remove-docker-images` to `docker-cleanup` and add docker builder prune for build cache cleanup
* Enhanced verbose mode with more detailed output for each step
