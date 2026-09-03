# mod_wsgi Changelog

## 6.0.6-3

- Add `mock/` directory with per-distro mock configs for EL8, EL9, EL10
  (x86_64 and aarch64) referencing the org-level casjay templates

## 6.0.6-2

- Replace unconditional RHEL-only macro defaults with full
  `%if 0%{?suse_version}` / `%else` / `%endif` block (mod_geoip pattern):
  - SUSE: apxs2, apache2-devel, /etc/apache2/conf.d, %{_libdir}/apache2
  - RHEL/Fedora: apxs, httpd-devel, /etc/httpd/conf.d, %{_libdir}/httpd/modules
- `BuildRequires: httpd-devel` replaced with `%{httpd_devel_pkg}` macro
- `Requires: httpd-mmn = %{_httpd_mmn}` guarded with
  `%if ! 0%{?suse_version}` in both python2 and python3 subpackages
  (apache2-devel on SUSE does not provide the httpd-mmn virtual package)

## 6.0.6-1

- Update to 6.0.6; fix Source0 tag URL for prefixed tag scheme

## 6.0.5-1

- Update to 6.0.5 (Source0 refs/tags/ URL verified 302->200)
- Drop Patch1 mod_wsgi-4.5.20-exports.patch (stale, was for 4.5.20)
- Remove commented-out mv/ln lines in %install
