# Bromite Builder

Utility script for building [Bromite](https://github.com/bromite/bromite) releases

- [Requirements](#requirements)
- [Setup](#setup)
- [Usage](#usage)
- [Notes](#notes)
- [Resources](#resources)

## <a name="requirements"></a>Requirements

- A 64-bit Intel machine running Linux with at least 8GB of RAM.
More than 16GB is highly recommended.
- At least 100GB of free disk space.
- Git and Python 2 for checking out and building Chromium
- Python 3 for [Ungoogled Chromium's](https://github.com/Eloston/ungoogled-chromium)
domain substitution utility. Only used when Bromite's
`Automated-domain-substitution.patch` fails to be applied

## <a name="setup"></a>Setup

Ubuntu users' systems will be bootstrapped via Chromium's
[`build/install-build-deps-android.sh`](https://chromium.googlesource.com/chromium/src.git/+/master/build/install-build-deps-android.sh)
if the `--ubuntu-install-build-deps` flag is set. It requires root permissions
and may install unwanted software.

All other distro users should follow Chromium's
[Notes For Other Distros](https://chromium.googlesource.com/chromium/src/+/master/docs/linux/build_instructions.md#notes)

Checking out the repo:
```shell
git clone https://github.com/nikolowry/bromite-builder.git; \
cd bromite-builder
```

## <a name="usage"></a>Usage

Usage instructions are always available by running `./bromite-builder -h` or
`./bromite-builder --help`

```
Usage: ./bromite-builder [command...] [options...]

Where optional [command] is one of:
  build, clean, fetch-sync, prepare, set-revision

If no [command] is set, the default command sequence will be executed:
  - set-revision
  - fetch-sync
  - prepare
  - build

Options:
  -a, --arch=<arch>
    Where <arch> is: arm, arm64, x86, x64.
    Defaults to arm

  -b, --bromite-git-url=<url>
    Where <url> is a Bromite Git repository.
    Defaults to https://github.com/bromite/bromite.git

  -g, --gn-args=<args>
    Where <args> is a string of GN build arguments

  -o, --output-dir=<dir>
    Where <dir> is a path to save the APK.
    Defaults to ./out

  -p, --patches-dir=<dir>
    Where <dir> is a path to a directory containing custom patches

  -t, --target=<target>
    Where Ninja <target> is: chrome_public_apk, system_webview_apk.
    Defaults to chrome_public_apk

  -r, --revision=<revision>
    Where <revision> is a Bromite release tag.
    Defaults to latest release

  -u, --upstream=<commit-hash>
    Where <commit-hash> is a long-format git commit.
    Defaults to master's HEAD.
    When set, any Chromium tag can be assigned to <revision>

  --no-bromite-patches
    Only apply patches from Bromite's chromium_patches_list.txt

  --no-skip-patches
    Exit on failed patch attempts

  --dark-navbar
    Prefer a dark navigation bar over a white one

  --ubuntu-install-build-deps
    Run Chromium's build/install-build-deps-android.sh during fetch-sync

  -h, --help
    Print help menu
```

## <a name="notes"></a>Notes

Builds produced with `bromite-builder` differ from official Bromite releases with
the following:

- Retains Chromium branding and namespace
- Build flag to revert the white Navigation Bar in the Material Design Refresh (MD2)
to black with option `--dark-navbar`
- GN args to default to disabled symbols for faster build times: 
`blink_symbol_level=0 symbol_level=0 enable_resource_allowlist_generation=false treat_warnings_as_errors=false`.

## <a name="resources"></a>Resources

- Bromite Repo: https://github.com/bromite/bromite
- Ungoogled Chromium Repo: https://github.com/Eloston/ungoogled-chromium
- Chromium Repo: https://chromium.googlesource.com/chromium/src.git/
- Chromium Android Build Docs: https://chromium.googlesource.com/chromium/src/+/master/docs/android_build_instructions.md
