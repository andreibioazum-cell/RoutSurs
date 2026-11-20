Thanks for contributing to RoutSurs!

Please describe what the change does and why it is needed.  If the change is
not RoutSurs-specific, consider sending it upstream to Buildroot first, so
that it can be merged here together with the next upstream sync.

Checklist:

- [ ] The change does not rename `BR2_*` symbols, directories or make targets
      (see BRANDING.md), unless it is part of a coordinated upstream rename.
- [ ] User-visible branding uses `$(BRAND_NAME)` / `$(BRAND_ID)` /
      `$(BRAND_VERSION)`, not a hard-coded string (see BRANDING.md).
- [ ] Copyright headers and license notices are preserved.
- [ ] `utils/check-package` was run on the changed files, if any package
      recipe, Config.in or defconfig was touched.
- [ ] The change was build-tested (at least the affected package or defconfig).

Documentation: docs/manual.  Licensing and attribution: COPYING, NOTICE.
