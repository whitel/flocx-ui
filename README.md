# Flocx-ui

Flocx plugin for horizon to show and create bids, offers, and contracts

> FLOCX provides a marketplace for trading physical servers among co-located pools of hardware where each pool is owned and managed by independent organizations. Using FLOCX, organizations can rent nodes from their co-located neighbors in times of high demand and offer their own resources at a suitable price when others experience high demand.

Read about the Flocx project [here](https://github.com/CCI-MOC/flocx).

* Free software: Apache license
* Release Notes: View the [changelog](CHANGELOG.md)
* Contributing: Read [CONTRIBUTING.md](CONTRIBUTING.md)

## Enabling in DevStack

Add this repo as an external repository into your `local.conf` file:

```conf
[[local|localrc]]
enable_plugin flocx https://github.com/CCI-MOC/flocx-ui

ADMIN_PASSWORD=secret
DATABASE_PASSWORD=$ADMIN_PASSWORD
RABBIT_PASSWORD=$ADMIN_PASSWORD
SERVICE_PASSWORD=$ADMIN_PASSWORD
```

## Manual Installation

The following below instructions assumes that Horizon is already installed and its installation folder is `<horizon>`. Detailed information on how to install Horizon can be found at [https://docs.openstack.org/horizon/latest/contributor/quickstart.html#setup](https://docs.openstack.org/horizon/latest/contributor/quickstart.html#setup).

The installation folder of Flocx-ui will be referred to as `<flocx-ui>`.

Flocx-ui uses [Node.js](https://nodejs.org) to run linters and JavaScript unit tests. Make sure to install Node.js before continuing.

---

Clone Flocx-ui

```bash
$ git clone https://github.com/CCI-MOC/flocx-ui
$ cd flocx-ui
```

Install requirements

```bash
$ npm install # This should install python dependencies as well
```

Install source code

```bash
$ sudo python setup.py install
```

Enable it in Horizon

```bash
$ ln -s <flocx-ui>/flocx_ui/enabled/_31000_flocx-ui.py <horizon>/openstack_dashboard/local/enabled
```

And restart the Apache server

```bash
$ sudo service apache2 restart
```

## Running tests

### Python tests

```bash
$ tox
```

### JavaScript tests

```bash
$ npm test
```
