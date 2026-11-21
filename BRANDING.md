RoutSurs branding
=================

This document describes how the distribution is named, where the name shows
up in a built image, and what must not be renamed.

Single source of truth
----------------------

The name and version of the produced operating system are defined once, at
the top of the top-level `Makefile`:

    BRAND_NAME    := RoutSurs
    BRAND_ID      := routsurs
    BRAND_VERSION := 1.0.0

`BR2_VERSION` is a different thing: it is the upstream Buildroot release this
tree is based on (for example `2026.11-rc1`) and it is kept in sync when
upstream is merged.  Both values are exported, so they are visible to
kconfig, to packages and to post-build scripts.

Where the brand is visible
--------------------------

| Location                         | Value                                            |
|----------------------------------|--------------------------------------------------|
| `make menuconfig` main menu      | `RoutSurs <BR2_VERSION> Configuration`           |
| `/etc/issue` (default)           | `Welcome to RoutSurs`                            |
| `/etc/hostname` (default)        | `routsurs`                                       |
| `/etc/os-release` `NAME`         | `RoutSurs`                                       |
| `/etc/os-release` `ID`           | `routsurs`                                       |
| `/etc/os-release` `ID_LIKE`      | `buildroot`                                      |
| `/etc/os-release` `VERSION`      | `<BRAND_VERSION> (Buildroot <BR2_VERSION>)`      |
| `/etc/os-release` `PRETTY_NAME`  | `RoutSurs <BRAND_VERSION> (Buildroot <BR2_VERSION>)` |
| `/etc/os-release` `BUILDROOT_VERSION` | full upstream-derived version string        |
| `make help`                      | refers to RoutSurs                               |
| `make release` tarball           | `routsurs-<BRAND_VERSION>.tar.*`                 |
| kconfig-generated `.config` head | `RoutSurs <version> Configuration`               |

Per-board configurations in `configs/` may still carry their own banner; only
the defaults in `system/Config.in` and the new
`configs/routsurs_aarch64_defconfig` are RoutSurs-branded.

Adding a new board
------------------

Copy an existing defconfig, then set at least:

    BR2_TARGET_GENERIC_HOSTNAME="routsurs"
    BR2_TARGET_GENERIC_ISSUE="Welcome to RoutSurs"

and keep the `BR2_DEFCONFIG` name in the `routsurs_*` namespace if the board is
maintained as part of RoutSurs.

What must not be renamed
------------------------

* `BR2_*` kconfig symbols, `BR2_EXTERNAL` and the `br2-` script prefix: they
  are the public interface shared with upstream Buildroot, external trees and
  existing defconfigs.
* Top-level directory layout (`arch/`, `board/`, `package/`, `support/`, ...).
* Make targets, package infrastructure macros (`generic-package`,
  `autotools-package`, ...) and `output/` layout.
* Copyright headers, `COPYING`, `DEVELOPERS`, `.mailmap`, `CHANGES`.
* Package recipes, patches and hashes of third-party software.

Renaming any of the above breaks upstream merges and build scripts, and would
falsify authorship.  New user-visible strings should use `$(BRAND_NAME)` /
`$(BRAND_ID)` / `$(BRAND_VERSION)` instead of hard-coding "RoutSurs" where a
Makefile is involved.

Attribution
-----------

RoutSurs is based on Buildroot.  All upstream copyright notices stay in place,
and the RoutSurs maintainers claim copyright only on the fork-specific
changes.  See `NOTICE` for the exact scope and for the license statement.
