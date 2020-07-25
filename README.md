# Ansible Role: redelk_redir

Role that helps setting up redirectors for RedELK project.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):
	# Common packages for RedHat and Debian
	common_pkgs:
	  - tmux
	  - rsync

	# pkgs for rhel
	rhel_pkgs:
	  - "{{ 'python3-policycoreutils' if (ansible_distribution_major_version | int >= 8) else 'policycoreutils-python' }}"
	  - rsyslog

	debian_pkgs:
	  - apt-transport-https
	  - python3-apt

	# Configure or not the firewall on your systems
	no_firewalling: true

	locale: en_US.UTF-8

	firewall:
	  redir_ports:
	    - 80/tcp
	    - 443/tcp

	# Your timezone
	timezone: Europe/Berlin

## Dependencies

	- src: robertdebock.epel
	- src: geerlingguy.filebeat
	- src: https://github.com/DrMeosch/ansible-role-python3
	  scm: git
	  version: master
	  name: drmeosch.python3

## Use with Ansible

```yaml
- hosts: all

  roles:
    - redelk_redir
```

## License

MIT / BSD

## Author Information

This role was created in 2020 by DrMeosch.
