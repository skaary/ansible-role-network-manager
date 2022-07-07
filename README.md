# Ansible Role: Network-Manager
[![CI](https://github.com/skaary/ansible-role-network-manager/actions/workflows/ci.yml/badge.svg?branch=main&event=push)](https://github.com/skaary/ansible-role-network-manager/actions?query=workflow%3Ci)

An Ansible Role that installs [Network-Manager](https://wiki.debian.org/NetworkManager) on Linux.

## Installation

Download the role directly from git by typing into your terminal:

```bash
$ ansible-galaxy install git+https://github.com/skaary/ansible-role-network-manager.git
```

or

```bash
$ ansible-galaxy install git+https://github.com/skaary/ansible-role-network-manager.git,,network_manager
```

to change the installed role name from *ansible-role-network-manager* to just *network_manager*.

Alternatively, install the role via a *requirements.yml* file, e.g. when installing multiple roles at once. See [ansible galaxy documentation](https://galaxy.ansible.com/docs/using/installing.html#installing-multiple-roles-from-a-file) for more information.

## Role variables

| Variable name                        | Default value | Description                                                                                                                                 |
| ------------------------------------ | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `network_manager_plugin_ssh`         | `true`        | Set to true to install the [ssh](https://www.ssh.com/academy/ssh) plugin for network-manager.                                               |
| `network_manager_plugin_openvpn`     | `true`        | Set to true to install the [openvpn](https://openvpn.net/community-resources/reference-manual-for-openvpn-2-4/) plugin for network-manager. |
| `network_manager_plugin_vpnc`        | `true`        | Set to true to install the [vpnc](https://linux.die.net/man/8/vpnc) plugin for network-manager.                                             |
| `network_manager_plugin_strongswan`  | `false`        | Set to true to install the [strongswan](https://linux.die.net/man/8/vpnc) plugin for network-manager.                                       |
| `network_manager_plugin_l2tp`        | `false`        | Set to true to install the [l2tp](https://en.wikipedia.org/wiki/Layer_2_Tunneling_Protocol) plugin for network-manager.                     |
| `network_manager_plugin_openconnect` | `false`        | Set to true to install the [openconnect](https://www.infradead.org/openconnect/manual.html) plugin for network-manager.                     |
| `network_manager_plugin_pptp`        | `false`        | Set to true to install the [pptp](https://datatracker.ietf.org/doc/html/rfc2637) plugin for network-manager.                                |
| `network_manager_nm_applet`          | `true`        | Set to true to install the GNOME GUI versions of the plugin packages.                                                                       |

## Example playbook

```yaml
- hosts: all
  vars:
    network_manager_plugin_strongswan: true
  roles:
    - ansible-role-network-manager
```

## Testing the role

### Vagrant

Vagrant can be used to test the role in order to graphically see it working in a virtual machine. Make sure Vagrant and VirtualBox are installed:

```bash
$ sudo apt install vagrant virtualbox
```

Use the following commands to run vagrant and boot up the virtual machine:

```bash
$ cd tests
$ vagrant up
```

Use `vagrant destroy` after you are done testing to delete the virtual machine. For more information about Vagrant and its commands, see the [Vagrant documentation](https://www.vagrantup.com/docs/cli).

### Molecule with Docker

Molecule can be used to test the role with a docker container. Make sure Molecule is installed:

```bash
$ python3 -m pip install --user "molecule[docker]"
```

Use the following commands to run Molecule in order to create the docker container and access the created container:
```bash
$ molecule converge && molecule login
```

For more information on how to use Molecule please consult the [Molecule documentation](https://molecule.readthedocs.io/en/latest/getting-started.html).

> Note: Python and Docker are required for the use of molecule. For more information, see [Molecule installation](https://molecule.readthedocs.io/en/latest/installation.html).

## License

MIT / BSD
