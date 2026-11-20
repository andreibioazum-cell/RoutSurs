# Security Policy

## RoutSurs

RoutSurs is a downstream distribution based on Buildroot.  Vulnerabilities
that are specific to RoutSurs (branding, default configurations, the
`routsurs_*` defconfigs, the `BRAND_*` handling, this repository's scripts)
should be reported privately to the RoutSurs maintainers through GitHub
security advisories:

https://github.com/andreibioazum-cell/RoutSurs/security/advisories/new

Please do not open a public issue for a security problem.

## Buildroot

The build engine, the package infrastructure and the package recipes are
upstream Buildroot code.  Vulnerabilities in that code affect upstream as
well, and should be reported upstream following the Buildroot security
policy:

- Advisories and discussion: https://lists.buildroot.org/mailman/listinfo/buildroot
- CPE: https://nvd.nist.gov/products/cpe/search/results?namingFormat=2.3&keyword=buildroot
- Upstream contact: security@buildroot.org (Buildroot maintainers only)

Upstream resources for tracking known vulnerabilities in the packages
included in generated images:

- https://nightly.buildroot.org/manual.html#_details_about_packages
- https://security.buildroot.org/
- https://autobuild.buildroot.org/stats/

## Vulnerabilities in packages

RoutSurs, like Buildroot, is a build system that cross-compiles packages from
third-party sources.  The maintainers are not responsible for security
vulnerabilities in those packages; report them to the upstream project that
maintains the affected package.  When a fix is available, a patch updating the
affected package can be sent to this repository (GitHub pull request) or to
upstream Buildroot.
