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
extend unbound /usr/bin/sudo /var/etc/snmp/unbound
```

## Notes
- You need to install `dhcpd-pools` or DHCP Stats won't work
- ZFS Stats requires you to install Perl JSON Module via `cpan JSON`
