## Changelog

### 0.1.12 (2018-05-27)
#### Added
- Added install_packages config option to allow installation of additional packages via apt-get
- Added install_nodes config option to help with installation of nodes
- Set default for install_nodes to node-red-contrib-home-assistant so automatically install node-red-contrib-home-assistant upon startup
- Added uninstall_nodes to help with removing nodes that are causing startup issues

#### Changed
- Changed base docker images to node-red-docker:v8 and nodered/node-red-docker:rpi-v8
- Switch password hash method from node-red-admin to bcryptjs


## Full Changelog

### 0.1.0 (2017-07-31)
#### Initial Release

### 0.1.1 (2017-08-10)
#### Added
- Option to enable SSL

### 0.1.2 (2017-09-15)
#### Changed
- Changed to use host network to allow Node-RED to listen on arbitrary ports

### 0.1.3 (2017-10-10)
#### Added
- Updated to support new hass.io build system

### 0.1.4 (2017-10-24)
#### Changed
- Updated webui links in config.json to support ssl when enabled in the addons

### 0.1.5 (2017-11-25)
#### Changed
- Moved data dir to /share/node-red
#### Added
- Added authentication for editor and admin API

### 0.1.6 (2017-12-13)
#### Changed
- node-red-admin no longer re-installs on every restart of the addon
#### Added
- Added authentication for HTTP nodes (Dashboard UI)

### 0.1.7 (2018-02-15)
#### Changed
- Bumping version to assist with upgrading to Node-RED v0.18.3

### 0.1.8 (2018-02-16)
#### Added
- Added support for [Node-RED Projects](https://nodered.org/docs/user-guide/projects/) in Node-RED v0.18.x

### 0.1.9 (2018-02-20)
#### Changed
- Upgrade node during build to address compatibility issue with node-red-contrib-home-assistant 0.3.0

### 0.1.10 (2018-02-20)
#### Added
- Added auto_uart permission which allows Node-RED nodes to access serial devices such as node-red-contrib-rfxcom.

### 0.1.11 (2018-03-21)
#### Changed
- Fixed how path to certs are escaped.

### 0.1.12 (2018-05-27)
#### Added
- Added install_packages config option to allow installation of additional packages via apt-get
- Added install_nodes config option to help with installation of nodes
- Set default for install_nodes to node-red-contrib-home-assistant so automatically install node-red-contrib-home-assistant upon startup
- Added uninstall_nodes to help with removing nodes that are causing startup issues

#### Changed
- Changed base docker images to node-red-docker:v8 and nodered/node-red-docker:rpi-v8
- Switch password hash method from node-red-admin to bcryptjs
