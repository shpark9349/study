[root@allinone ~(keystone_admin)]# cat /etc/neutron/dhcp_agent.ini |grep -Ev "^#|^$" | sed -e "s/^\[/\n\[/g"

[DEFAULT]
interface_driver = neutron.agent.linux.interface.OVSInterfaceDriver
resync_interval = 30
dhcp_driver = neutron.agent.linux.dhcp.Dnsmasq
enable_isolated_metadata = False
enable_metadata_network = False
debug = False
root_helper=sudo neutron-rootwrap /etc/neutron/rootwrap.conf
state_path=/var/lib/neutron

[AGENT]
