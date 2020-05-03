# ansible-role-pi4

This role fine tunes [Raspberry Pi 4](https://www.raspberrypi.org/).

## Description

This role can blacklist certain modules if wished.
For example, you can blacklist modules to disable WiFi or Bluetooth to save some energy/money.

If modules for WiFi or Bluetooth are disabled. This role auto-detects this and disables certain services.

For Wifi it's `wpa_supplicant` services and Bluetooth it's `hciuart`

## Role Variables


| Name                             | Default | Description                                                                                                     |
| :------------------------------- | :-----: | --------------------------------------------------------------------------------------------------------------- |
| `raspberry_pi_reboot`            |  true   | Allows the role to reboot the system.                                                                           |
| `raspberry_pi_blacklist_modules` |   []    | List of modules to Blacklist. e.g. Disable WiFi `[brcmfmac, brcmutil]` or disable Bluetooth `[btbcm, hci_uart]` |

## Role Tags

| Name                     | Description                 |
| ------------------------ | --------------------------- |
| `raspberry_pi_all`       | Tag to run all tasks.       |
| `raspberry_pi_preflight` | Tag to run preflight tasks. |
| `raspberry_pi_configure` | Tag to run configure tasks. |

## Dependencies

**None**

## Example Playbook


```yaml
- name: All
  hosts: all
  debugger: on_failed
  roles:
    - role: ansible-role-raspberry-pi
      vars:
        raspberry_pi_blacklist_modules:
          - brcmfmac  # disable WiFi
          - brcmutil  # disable WiFi
          - btbcm     # disable Bluetooth
          - hci_uart  # disable Bluetooth
```

## License

MIT License

## Contributors

Daniel von Essen
