# librenms-snmp-pfsense
LibreNMS Agent SNMP Extension Scripts for pfsense

## Prequisites
1. Install the `net-snmp` package via the package manager
2. Install Git via the CLI `pkg install git`

## Installation
1. `cd /var/etc && git clone https://github.com/spyfly/librenms-snmp-pfsense.git snmp
2. Add the following lines under Custom Options in the netsnmp UI: 
```
extend dhcpstats /var/etc/snmp/dhcp.py
extend zfs /var/etc/snmp/zfs-freebsd
extend unbound /usr/local/bin/sudo /var/etc/snmp/unbound
extend smart /usr/local/bin/sudo /var/etc/snmp/smart
extend freeradius /var/etc/snmp/freeradius.sh
extend ntp-server /var/etc/snmp/ntp-server.sh
```

## Notes
- You need to install `dhcpd-pools` or DHCP Stats won't work
- ZFS Stats requires you to install Perl JSON Module via `cpan JSON`
- Unbound Stats require you to run `unbound-control-setup` first and install sudo via `pkg install sudo`
- SMART Stats require config file generation via `/var/etc/snmp/smart -g > /var/etc/snmp/smart.config`
- FreeRADIUS Stats require you to [enable the stats service](https://docs.librenms.org/Extensions/Applications/#freeradius) first