# Maximize available disk space for build tasks

Modified version of [easimon/maximize-build-space], this fork only removes unwanted software from GitHub runner CI.

By default, public shared Github runners come with around `25-29 GB` of free disk space to be consumed by your build job.
If this is too little for you, and your build job runs out of disk space, this action might be for you.

If not: please go on, there's nothing to see here.

This action maximizes the available disk space on public shared GitHub runners, by

- Optionally removing unnecessary preinstalled software
- Optionally removing the swapfile
- Optionally setting `TMPDIR` environment variable to point to the ephemeral disk mount (`/mnt`)

This shall make you gain around `32 GB` on Ubuntu 22.04 <!-- TODO: verify this info for 24.04 -->

The idea came up when I tried to build a Ubuntu Linux Kernel DEB on Github, and the Job aborted due to disk space issues.

## Caveats

- **This action is a hack, really**, and on a "works for me" basis. It has been built by modifying [easimon/maximize-build-space] and reverse-engineering undocumented parts of the Github runner setup, which might change in the future -- up to the point where this action ceases to work. For sure you're voiding the warranty on Github runners when using this. **If you are not running into disk space issues with the default runner setup, don't use it.**.
- Removal of unnecessary software is currently implemented by `rm -rf` on specific folders, not by using a package manager or anything sophisticated. While this is quick and easy, it might delete dependencies that are required by your job and so break your build (e.g. because your build job uses a .NET based tool and you removed the required runtime).

## How it works

At the time of writing, public [Github-hosted runners](https://docs.github.com/en/actions/concepts/runners/github-hosted-runners) are using [Azure DS2_v2 virtual machines](https://docs.microsoft.com/en-us/azure/virtual-machines/dv2-dsv2-series#dsv2-series), featuring a `84 GB` OS disk on `/` and a `14 GB` temp disk mounted on `/mnt`.

1. The root file system has `~29 GB` (of `84 GB`) available, the rest being consumed by the preinstalled build environment. Github runners come with a rich choice of software, see the image descriptions for [Ubuntu 22.04](https://github.com/actions/runner-images/blob/main/images/ubuntu/Ubuntu2204-Readme.md) or [Ubuntu 24.04](https://github.com/actions/runner-images/blob/main/images/ubuntu/Ubuntu2404-Readme.md). This is great to support a wide variety of workflows out of the box, but also consumes a lot of space by providing programs that might be unnecessary for an individual build job.

This action does the following:

1. (Optionally) removes unwanted preinstalled software and the swapfile
1. (Optionally) sets `TMPDIR` environment variable to point to `/mnt`, so that temporary files created by build tools are stored on the ephemeral disk instead of the root disk.

This results in the space of the previously installed packages (around `32 GB`) available for your build job.

## Usage

You should most probably use this action as the first build step, even **before** `actions/checkout`. Since this action mounts a volume over the current working directory by default, the current content of the working directory will be inaccessible afterwards.

With the default configuration, you won't gain any disk space. You can remove software that is unnecessary for your build job.
<!-- TODO: add examples how much space each option gains. -->

When removing software, consider that the removal of large amounts of files (which this is) can take minutes to complete. On the upside, you'll get around `32 GB` of disk space available if you actually need it.

```yaml
name: My workflow that requires a lot of disk space
on: push

jobs:
  build:
    name: Build my artifact
    runs-on: ubuntu-latest
    steps:
      - name: Maximize build space
        uses: nepalevov/maximize-build-space@main
        with:
          remove-android: 'true'
      - name: Checkout
        uses: actions/checkout@v4

      - name: Build
        run: |
          echo "Free space:"
          df -h
```

## Inputs

<!-- TODO: add inputs table -->

<!-- TODO: Document how much space each option frees. -->

[easimon/maximize-build-space]: https://github.com/easimon/maximize-build-space
