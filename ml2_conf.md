[root@allinone ~(keystone_admin)]# cat /etc/neutron/plugins/ml2/ml2_conf.ini |grep -Ev "^#|^$" | sed -e "s/^\[/\n\[/g"

[DEFAULT]

[ml2]
type_drivers = flat,vxlan
tenant_network_types = vxlan
mechanism_drivers =openvswitch
path_mtu = 0

[ml2_type_flat]
flat_networks = *

[ml2_type_geneve]

[ml2_type_gre]

[ml2_type_vlan]

[ml2_type_vxlan]
vni_ranges =1001:2000
vxlan_group = 239.1.1.2

[securitygroup]
firewall_driver = neutron.agent.linux.iptables_firewall.OVSHybridIptablesFirewallDriver
enable_security_group = True
