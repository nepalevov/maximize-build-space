# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

Initial release

### Added

- Enforce megabytes in `df` command output if `verbose` is set - more precise for results comparison
- New `set-tmpdir` option to set TMPDIR environment variable to `/mnt` for ephemeral disk storage usage
- New `remove-java` option to remove Java JDK (Temurin), Ant, Gradle and Maven
- New `remove-swift` option to remove Swift toolchain
- New `remove-julia` option to remove Julia
- New `remove-browsers` option to remove Firefox, Chromium, Chrome and Edge (browsers and webdrivers)
- New `remove-cloud-tools` option to remove AWS CLI, Azure CLI, and Google Cloud CLI (keeps GitHub CLI)
- New `remove-kubernetes-tools` option to remove kubectl, helm, kind, minikube and kustomize
- New `remove-powershell` option to remove PowerShell and PowerShell modules (Az modules, etc.)
- New `remove-container-tools` option to remove podman, buildah, skopeo and containernetworking-plugins
- New `remove-rust` option to remove Rust, rustup and cargo
- New `remove-python` option to remove pipx and miniconda
- New `remove-node` option to remove Node.js
- New `remove-go` option to remove Go language
- New `remove-ruby` option to remove Ruby language
- Renamed `remove-docker-images` to `docker-cleanup` and add docker builder prune for build cache cleanup
- Enhanced verbose mode with more detailed output for each step
