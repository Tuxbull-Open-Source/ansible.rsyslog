# Ansible rsyslog role

Install `rsyslog`, manage one forwarding configuration fragment, validate it
before activation, and enable the service.

## Requirements

- Ansible 2.15 or later.
- A supported RHEL-family, Debian, or Ubuntu target.
- A reachable log receiver when forwarding is required.

## Variables

| Variable | Default | Description |
| --- | --- | --- |
| `rsyslog_server_cfg` | `@@logs.example.invalid:1514` | Rsyslog action: `@@` is TCP, `@` is UDP. |
| `rsyslog_cfg_name` | `99-rsyslog-forwarder` | Fragment basename below `/etc/rsyslog.d/`. |

The role renders the following directive:

```text
*.* <rsyslog_server_cfg>
```

Override it with an approved receiver address. Do not place production internal
addresses in this public role.

## Example

```yaml
---
- hosts: linux
  become: true
  roles:
    - role: tuxbull.rsyslog
      vars:
        rsyslog_server_cfg: '@@logs.example.invalid:1514'
```

## Validation and limitations

The role runs `rsyslogd -N1` against the rendered fragment before installing it
and restarts rsyslog only when the configuration changes. It does not configure
a receiver, TLS certificates, queue persistence, log rotation, or receiver-side
delivery guarantees. Verify network reachability and receiver ingestion
separately.

## License

[GPL-3.0-only](https://www.gnu.org/licenses/gpl-3.0.html)
