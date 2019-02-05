# Rancher 2 cloudscale.ch UI Driver

[![Build Status](https://api.travis-ci.com/splattner/ui-driver-cloudscale.svg?branch=master)](https://travis-ci.com/splattner/ui-driver-cloudscale)


Rancher 2 UI driver for [cloudscale.ch](https://www.cloudscale.ch)

## Using

* Add a Machine Driver in Rancher 2 (Global -> Node Drivers)

| Key | Value |
| --- | ----- |
| Download URL | `https://github.com/splattner/docker-machine-driver-cloudscale/releases/download/v0.0.2/docker-machine-driver-cloudscale_v0.0.2_linux_amd64.tar.gz` |
| Custom UI URL | `https://s3.eu-central-1.amazonaws.com/cloudscale-rancher-v2-ui-driver/component.js` |
| Whitelist Domains |  `s3.eu-central-1.amazonaws.com` |
| Engine Options -> Docker Install URL | `https://get.docker.com/`|

The recommended one `https://releases.rancher.com/install-docker/17.03.sh`, seems not to work.


* Wait for the driver to become "Active"
* Go to Clusters -> Add Cluster, your driver and custom UI should show up.

![Authentication screen](docs/authentication-screen.png)
![Configuration screen](docs/configuration-screen.png)
![Add Cluster screen](docs/add-cluster.png)


## Development

This package contains a small web-server that will serve up the custom driver UI at `http://localhost:3000/component.js`. You can run this while developing and point the Rancher settings there.
* `npm start`
* The driver name can be optionally overridden: `npm start -- --name=DRIVERNAME`
* The compiled files are viewable at http://localhost:3000.
* **Note:** The development server does not currently automatically restart when files are changed.

## Building

For other users to see your driver, you need to build it and host the output on a server accessible from their browsers.

* `npm run build`
* Copy the contents of the `dist` directory onto a webserver.
  * If your Rancher is configured to use HA or SSL, the server must also be available via HTTPS.
