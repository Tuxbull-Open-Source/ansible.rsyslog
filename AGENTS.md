# Repository instructions

This repository provides the reusable `tuxbull.rsyslog` Ansible role. Keep it
focused on package installation, forwarding configuration, and service
management. Do not commit real receiver addresses, credentials, certificates,
inventories, lab artifacts, or internal logs.

Use the deterministic upstream `joe-speedboat/ansible.template` dispatcher.
Validate YAML, syntax, rendered `rsyslogd -N1` configuration, service state,
and second-run idempotency in the default disposable Linux lab. A green sender
role run does not prove the remote receiver ingested messages; verify that
separately only when an approved receiver exists.

`README.md` is usage documentation. `CHANGELOG.md` is release history. Source
repository is `Tuxbull-Open-Source/ansible.rsyslog`; Galaxy FQN is
`tuxbull.rsyslog`. Do not self-merge. After review and merge, create a
three-component SemVer tag and matching published GitHub Release, then import
and verify unpinned and pinned Galaxy installations.
