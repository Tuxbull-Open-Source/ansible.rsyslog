# Changelog

## v1.0.0 - 2026-10-27

### Changed

- Migrate the role to `tuxbull.rsyslog` and current Galaxy metadata.
- Align dispatcher files with `joe-speedboat/ansible.template`.
- Use fully qualified modules, package `present` state, validated template
  rendering, handlers, and systemd service management.
- Replace the private default receiver with a public-safe placeholder.

### Verified

- Live disposable Linux-lab package, configuration, service, syntax, and
  idempotency validation.
