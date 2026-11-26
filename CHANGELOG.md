# Changelog

## [1.2.0](https://github.com/nepalevov/maximize-build-space/compare/v1.1.0...v1.2.0) (2026-11-26)


### Features

* add runner OS check, skip unsupported with warning ([29f3092](https://github.com/nepalevov/maximize-build-space/commit/29f30923d66ae40836921c653754ccfd14cb4fae))


### Bug Fixes

* enhance TMPDIR validation with detailed warnings for unsupported conditions ([f61a774](https://github.com/nepalevov/maximize-build-space/commit/f61a7744b54ed15ec2eb5a9eef214ba4c36fef29))
* pass inputs to scripts via env to avoid shell injection and empty-value errors ([525cc9d](https://github.com/nepalevov/maximize-build-space/commit/525cc9dccfda613e411dc0ba15cc4a38476db5f6))
* quote arguments in dpkg command to catch all packages to be removed ([#19](https://github.com/nepalevov/maximize-build-space/issues/19)) ([576a524](https://github.com/nepalevov/maximize-build-space/commit/576a52458586600d137a1de0814072035426675a))
* remove only installed apt packages ([d8ec2b3](https://github.com/nepalevov/maximize-build-space/commit/d8ec2b31b761688e78b6d64f97f3bc213b8cfeed))
* remove the actual swap files instead of a hard-coded /mnt/swapfile ([8cdbe36](https://github.com/nepalevov/maximize-build-space/commit/8cdbe36ac64679e9ce0942a59a52dfcc5d4d1277))
* set TMPDIR to /mnt only when it is a separate disk ([60ddf3b](https://github.com/nepalevov/maximize-build-space/commit/60ddf3b050fa4d8251d085b71bb308594cae9c65))

## [1.1.0](https://github.com/nepalevov/maximize-build-space/compare/v1.0.1...v1.1.0) (2026-01-20)


### Features

* use dpkg output to define what packages to remove ([146a347](https://github.com/nepalevov/maximize-build-space/commit/146a347aa2882b9c4ebf64bd7b23a824213d0b02))


### Bug Fixes

* add --autoremove flag for apt-get ([357f889](https://github.com/nepalevov/maximize-build-space/commit/357f8894781cccaf3180b411ea91a3b3f36f4bdb))

## [1.0.1](https://github.com/nepalevov/maximize-build-space/compare/v1.0.0...v1.0.1) (2025-11-06)


### Bug Fixes

* set write permissions for /mnt dir if used ([d9175b3](https://github.com/nepalevov/maximize-build-space/commit/d9175b3e22b70eef5f0837bd94ca3cb01d6ff097))

## [1.0.0](https://github.com/nepalevov/maximize-build-space/compare/v1.0.0...v1.0.0) (2025-11-06)


### Features

* release 1.0.0 ([d9c7251](https://github.com/nepalevov/maximize-build-space/commit/d9c7251e92f088ff975a41b5dfb9a6aaaea1c7ac))
