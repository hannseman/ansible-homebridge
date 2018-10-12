# ansible-homebridge

This role will setup and configure a [Homebridge](https://github.com/nfarina/homebridge) installation. 

It will install Node.js. 
It will run homebridge in a secured systemd service as the user `homebridge`. 
It will allow you to configure your accessories and platforms using yaml.

## Variables

```yaml
# The homebridge version to run
homebridge_version: 0.4.45
# The homebridge user home directory
homebridge_dir: /var/homebridge
# Path to homebridge
homebridge_bin: /usr/bin/homebridge
# The homebridge environment file
homebridge_defaults: /etc/default/homebridge
# What port to run homebridge under
homebridge_port: 51826
# If homebridge should run in debug mode
homebridge_debug: false
# Node.js version to run homebridge under
homebridge_nodejs_version: "8.x"
# Path to Node.js
homebridge_nodejs_binary: /usr/bin/node
# To configure PartOf= in homebridge systemd service
homebridge_systemd_part_of_service:
# Enable CAP_NET_RAW
homebridge_enable_cap_net_raw: false
# Homebridge config.json (see https://github.com/nfarina/homebridge/blob/master/config-sample.json) 
homebridge_name: Homebridge
homebridge_username: CC:22:3D:E3:CE:30
homebridge_pin: 123-45-678
homebridge_accessories: []
homebridge_platforms: []
```

## Example Playbook
```yaml
- hosts: servers
  roles:
     - hannseman.homebridge
  vars:
    homebridge_plugins:
    - name: homebridge-dummy
      version: 0.3.0
    homebridge_accessories:
    - accessory: "DummySwitch"
      name: "My Switch 1"
```
