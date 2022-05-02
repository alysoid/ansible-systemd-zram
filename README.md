# [Catena](https://github.com/alysoid/catena) Ansible Role: systemd-zram

Manage [systemd-zram](https://man.archlinux.org/man/community/zram-generator/zram-generator.8.en) service generator for zram devices. [zram-generator](https://github.com/systemd/zram-generator) is a generator that creates systemd units to format and use compressed RAM devices, either as swap or a file system.

## Role variables

### `systemd_zram`

Manage [zram-generator.conf](https://man.archlinux.org/man/zram-generator.conf.5) - Systemd unit generator for zram swap devices.

Configuration files will have the .conf extension and will be placed in the configuration snippets directory `/etc/systemd/zram-generator.conf.d`. These configuration files can control zram devices. The following example enables `zram0` device with `lz4` (default is `lzo-rle`) compression:

```yaml
# Default
systemd_zram: []

# Example
systemd_zram:
  # /etc/systemd/zram-generator.conf.d/zram0.conf
  - name: zram0
    options:
      # The size of the zram device in MiB
      zram_size: "256"
      # Compression algorithm: lzo, lz4, zstd, lzo-rle
      compression_algorithm: lz4
```

### `systemd_zram_cleanup`

When `true`, remove all existing configuration files before creating the new ones.

```yaml
# Default
systemd_zram_cleanup: false
```
