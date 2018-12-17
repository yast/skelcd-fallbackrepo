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
  is a multibuild package. Add the product name (`FOO`) to
  [`_multibuild`](https://build.opensuse.org/package/view_file/system:install:head/skelcd-fallbackrepo/_multibuild).

2. Adjust
  [skelcd-fallbackrepo.spec](https://build.opensuse.org/package/view_file/system:install:head/skelcd-fallbackrepo/skelcd-fallbackrepo.spec) and
  add a new `%theme` macro matching your product. The product name from `_multibuild` is visible as `%flavor` in the spec file.
  Be careful as not every product is built on every architecture.

2. Add `skelcd-fallbackrepo-FOO` to the `BuildRequires` of the spec file of
  [`installation-images`](https://github.com/openSUSE/installation-images).
  [installation-images.spec](https://build.opensuse.org/package/view_file/system:install:head/installation-images/installation-images.spec) is
  maintained in the OBS. Again, be careful as not every product is available on every architecture.

`skelcd-fallbackrepo` itself does not contain any sources beside the spec file.
