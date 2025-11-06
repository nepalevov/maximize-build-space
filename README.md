# Maximize Build Space

Free up to **42 GB** of additional disk space on GitHub Actions runners by removing unnecessary preinstalled software.

GitHub-hosted runners provide approximately **22 GB** of free disk space by default. If your build requires more space, this action can help by removing unused software packages and optimizing disk usage.

## Caveats

- **This action is a hack, really**, and on a "works for me" basis. Runner configuration might change in the future - up to the point where this action ceases to work
- For sure you're voiding the warranty on Github runners when using this
- Removal of unnecessary software is currently implemented by `rm -rf` on specific folders, only a fraction by a package manager, and definitely by nothing sophisticated. While this is quick and easy, it might delete dependencies that are required by your job and so break your build

## How it works

GitHub-hosted runners use [Azure Standard_D4ads_v5 virtual machines](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes/general-purpose/dadsv5-series) with:

- **75 GB** OS disk mounted on `/`
- **75 GB** temp disk mounted on `/mnt`

Of the `72 GB` root filesystem, only `~22 GB` is available by default. The remainder is consumed by preinstalled build tools and software. See [GitHub runner images](https://github.com/actions/runner-images/blob/main/images/ubuntu/) for details on what's included.

This action frees up space by:

1. (Optionally) removes unwanted preinstalled software
1. (Optionally) disables & removes the swapfile
1. (Optionally) sets `TMPDIR` environment variable to point to `/mnt`, so that temporary files created by build tools are stored on the ephemeral disk instead of the root disk

Result: Up to `42 GB` of additional space becomes available for your builds

## Statistics

<!-- TODO: add a table with statistics how much space each option gains and how long it takes to complete -->

## Usage

> [!note]
> All removal options are **disabled by default**. Enable only the options your build requires

> [!tip]
> More enabled options = longer execution time. Balance space needs with workflow performance

```yaml
name: Build with Extended Disk Space
on: push

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Maximize build space
        uses: nepalevov/maximize-build-space@v1 # x-release-please-major
        with:
          remove-android: 'true'
          # Other options as needed
      - name: Checkout
        uses: actions/checkout@v5
      - name: Build
        run: |
          echo "Available disk space:"
          df -h
```

## Inputs

See [`action.yml`](action.yml) for a complete list of available removal options.

<!-- TODO: add inputs table with description and defaults  -->

## Credits

Inspired by:

- [easimon/maximize-build-space](https://github.com/easimon/maximize-build-space)
- [AdityaGarg8/remove-unwanted-software](https://github.com/AdityaGarg8/remove-unwanted-software)
- [ublue-os/remove-unwanted-software](https://github.com/ublue-os/remove-unwanted-software)
- [apache/pulsar clean-disk action](https://github.com/apache/pulsar/blob/ed5dbb5289f09f913f07a38ba1481727f00f063a/.github/actions/clean-disk/action.yml)
