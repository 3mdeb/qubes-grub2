Qubes OS grub2 package
======================

This is a fork of qubes-grub2 with additional support for TrenchBoot.

## Introduced modifications:

- Changed the GRUB2 version to 2.04~rc1
- Added 3mdeb developer keys
- Changed the source to 3mdeb generated and signed GRUB2 packages with
  TrenchBoot support
- Added slaunch module to module list

## Installation HOWTO


1. Clone [qubes-builder](https://github.com/QubesOS/qubes-builder)

```
git clone https://github.com/QubesOS/qubes-builder.git
cd qubes-builder
```

2. Use your desired `builder.conf` file from `example-configs` directory.

3. Edit the `builder.conf` by adding:

```
NO_SIGN ?= 1
NO_CHECK ?=

GIT_URL_grub2=https://github.com/3mdeb/qubes-grub2
BRANCH_grub2=trenchboot_support
```

4. Download sources used to build Qubes:

```
make get-sources
```

5. Install dependencies:

```
make install-deps
```

6. Build the GRUB2 RPM packages:

```
make grub2
```

7. The result will be placed as RPM package in:
   `qubes-builder/qubes-src/grub2/pkgs/dom0-fc31/{x86_64,noarch}`. It may be
   transferred to Dom0 and installed.

8. After RPM packages are installed in Dom0 invoke:

```
sudo grub2-install /dev/sdX
```

where X is your main disk with Qubes OS boot partition.
