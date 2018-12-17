## skelcd-fallbackrepo

`skelcd-fallbackrepo-FOO` are packages containing (one package per product
`FOO`) a fallback repository that is used by the installer to get meta data about
the product the user selects before registration.

Currently it consists of two packages (per product):

- `skelcd-control-FOO`
- `FOO-release`

Historically, the actual spelling of `FOO` may differ in both packages.

The re-packaging is necessary as `FOO-release` packages conflict with each other.

To support a new product `FOO`:

1. Create a new sub-package of `skelcd-fallbackrepo` named
  `skelcd-fallbackrepo-FOO`. This is relatively easy as `skelcd-fallbackrepo`
  is a multibuild package. The package is maintained in the OBS. The spec file is
  [here](https://build.opensuse.org/package/view_file/system:install:head/skelcd-fallbackrepo/skelcd-fallbackrepo.spec),
  the multibuild definitions are
  [here](https://build.opensuse.org/package/view_file/system:install:head/skelcd-fallbackrepo/_multibuild).

2. Add `skelcd-fallbackrepo-FOO` to the spec file of
  [`installation-images`](https://github.com/openSUSE/installation-images). The spec file
  is maintained in the OBS
  [here](https://build.opensuse.org/package/view_file/system:install:head/installation-images/installation-images.spec).

`skelcd-fallbackrepo` itself does not contain any sources beside the spec file.
