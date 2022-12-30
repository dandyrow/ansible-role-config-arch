Ansible Role - Config_Arch
=========

Configures a fresh Arch install. Intended to carry out the tasks which are to be run in an arch-chroot environment after pacstrap is run.

Install from Ansible Galaxy using this command: `ansible-galaxy install dandyrow.config_arch`.

View Ansible Galaxy page [here](https://galaxy.ansible.com/dandyrow/config-arch).

Role Variables
--------------

The following variables, defined in defaults/main.yml, should be set to your preference as shown in the example playbook below.

The following two varaibles are used in combination with each other to set the system timezone:
* `region: Europe` - Region for setting your timezone. Must be a valid region found in `/user/share/zoneinfo/`

* `city: London` - City for setting your timezone. Must be a valid city found in `/user/share/zoneinfo/{{ region }}/`, where `{{ region }}` is what the above variable is set to.

The following two variables are used in combination with each other to set the system locale:
* `locale: en_GB.UTF-8` - The locale to set the system to. Must be a locale found in `/etc/locale.gen`.

* `character_set: UTF-8` - The character set to set the system to. Found in the same file as the values for the variable above. 

`keymap: uk` - The keymap to set the system to. Available keymaps can be viewed using this command: `# ls /usr/share/kbd/keymaps/**/*.map.gz`.

`hostname: arch` - Hostname of the system.

`auto_update_systemd_boot: true` - Whether to set systemd-boot to auto update.

`install_cloudinit: true` - Whether to install and enable cloud-init.

The following variables, defined in vars/main.yml, should not need to be set by the user and are defined here to allow users to check no other roles or playbooks overwrite it.

`cloud_init_packages: [ cloud-init, cloud-guest-utils ]` - The names of the packages required to install cloud-init.

Supported Platforms
-------------------

* Arch Linux

Example Playbook
----------------
```yaml
    - hosts: servers
      roles:
        - role: dandyrow.config_arch
          vars:
            region: Asia
            city: Tokyo
            hostname: Desktop-System
            install_cloudinit: false
```
License
-------

GPL-3.0-only

Contributing
------------

To contribute to the project please fork it, make your changes then open a pull request. Your changes will be considered for merging provided it passes all CI tests. If any changes are required before merging these will be discussed in the pull request discussion thread.

Author Information
------------------

Created by Daniel Lowry (dandyrow).

Email: [development@daniellowry.co.uk](mailto:development@daniellowry.co.uk)
