# Node-RED Hass.io Add-On
---------

[Hass.io](https://home-assistant.io/hassio/) add-on for [Node-RED](https://nodered.org/).

## Installation

* Add the Hass.io add-on repository `https://github.com/notoriousbdg/hassio-addons`
* Select the "Node-RED" add-on
* Click on Install

## Addon Configuration
| Option  | Default  | Description |
| ------------ | ------------ | ------------ |
| ssl | `false` | If changed to true, SSL/TLS will be enabled |
| certfile | `fullchain.pem` | Relative path in /ssl to certificate chain |
| keyfile | `privkey.pem` | Relative path in /ssl to certificate private key |
| users | `[ { "username": "admin", "password": "password", "permissions": "*" } ]` |  Array of users allowed to login to the flow editor.  Set to `[]` to disable authentication |
| http_node_user |  `[ { "username": "admin", "password": "password" } ] ` | User allowed to login to the Dashboard UI.  Set to `[]` to disable authentication |
| projects | false | Enable projects feature in v0.18.x by setting to `true`. Refer to [Node-RED Projects](https://nodered.org/docs/user-guide/projects/) for additional info about setting up projects. |
| install_packages | `[]` | Array of packages to install via apt-get.  E.g. `[ "package1", "package2"]` |
| install_nodes | `[ "node-red-contrib-home-assistant" ]` | Array of nodes to install via npm.  E.g. `[ "node-red-dashboard", "node-red-contrib-vacation-timer"]`.  To force install of a specific version of a node add version after node name. E.g. `[ "node-red-contrib-home-assistant@0.3.2" ]`  Note: Manage Palatte can still be used within Node-RED if desired.|
| uninstall_nodes | `[]` | Nodes that are causing startup issues can be removed using this option.  E.g. `[ "node-red-admin" ]` |

## Node-RED Configuration
The [node-red-contrib-home-assistant](https://flows.nodered.org/node/node-red-contrib-home-assistant) nodes for Node-RED to connect to Home Assistant should be installed by default.  When configuring your first flow, you will be prompted to configure a Home Assistant connection.

**It is strongly recommended to use the Hass.io API Proxy address of `http://hassio/homeassistant` with no password as Home Assistant server address (server node Base URL) as it does not require any special DNS, port forwarding, or SSL configuration**.

## Home Assistant UI Integration
* Configure [panel_iframe](https://home-assistant.io/components/panel_iframe/) component to embed Node-RED UI into Home Assistant UI using this example:

    ```yaml
    panel_iframe:
      nodered_flows:
        title: 'Node-RED Flows'
        url: 'http://hassio.local:1880'
        icon: mdi:nodejs
    ```

* If you install [Node-RED Dashboard](https://github.com/node-red/node-red-dashboard) in Node-RED, you can expose the dashboard in the [Hass.io](https://home-assistant.io/hassio/) UI using this example to your [panel_iframe](https://home-assistant.io/components/panel_iframe/) section:

    ```yaml
    panel_iframe:
      nodered_ui:
        title: 'Node-RED Dashboard'
        url: 'http://hassio.local:1880/ui'
        icon: mdi:nodejs
    ```

## Support

Please use [this thread](https://community.home-assistant.io/t/repository-notoriousbdg-add-ons-node-red-and-ha-bridge/23247) for feedback or submit an [issue on GitHub](https://github.com/notoriousbdg/hassio-addons/issues).

## FAQ

### Q: How do I update to the latest version of Node-RED ASAP?
A: Since this addon is derived from the official Node-RED docker image, you may need to manually force hassio to rebuild the image to get the latest Node-RED version. To force a rebuild of the image to upgrade Node-RED, navigate to http://hassio.local:8123/hassio/addon/27e642c6_nodered then click on "Rebuild".

### Q: How do I update builtin nodes when updating via "Manage palette" fails?
A: The builtin nodes can be updated by manually force hassio to rebuild the image to get the latest Node-RED version. To force a rebuild of the image to upgrade Node-RED, navigate to http://hassio.local:8123/hassio/addon/27e642c6_nodered then click on "Rebuild".

### Q: Why can't Node-RED connecto to Home Assistant when SSL is enabled?
A: There are many potential reasons, which are motly caused by DNS or NAT loopback. The best option to workaround these issues is to configure Node-RED to use `http://hassio/homeassistant` instead of your private IP or DNS name.

### Q: Why is Node-RED inaccessible when internet access is down?
A: This can be caused by DNS failures because Home Assistant's public DNS name was used in Node-RED.  The best option to workaround this issue is to configure Node-RED to use `http://hassio/homeassistant` instead of your private IP or DNS name.
