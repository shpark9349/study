[root@allinone ~(keystone_admin)]# cat /etc/neutron/l3_agent.ini |grep -Ev "^#|^$" | sed -e "s/^\[/\n\[/g"

[DEFAULT]
interface_driver = neutron.agent.linux.interface.OVSInterfaceDriver
agent_mode = legacy
external_network_bridge =
debug = False

[AGENT]
