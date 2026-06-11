add the wakizashi zmk config repository by modifying your `west.yml` file in `/config`. then, add a copy of the `.conf` file and the `.keymap` file, also in the `/config` folder.

```
manifest:
  remotes:
    - name: zmkfirmware
      url-base: https://github.com/zmkfirmware
    # Add the base GitHub URL as a remote.
    - name: newx-it
      url-base: https://github.com/newx-it
  projects:
    - name: zmk
      remote: zmkfirmware
      revision: main
      import: app/west.yml
    # Add the name of the repository as a project.
    - name: zmk-keyboard-wakizashi
      remote: newx-it
      revision: main
  self:
    path: config
```

to build the firmware, add the following to your `build.yaml`:

```
---
include:
- board: xiao_ble//zmk
  shield: wakizashi
  snippet: studio-rpc-usb-uart
  cmake-args: -DCONFIG_ZMK_STUDIO=y
```
