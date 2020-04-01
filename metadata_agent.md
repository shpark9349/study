[root@allinone ~(keystone_admin)]# cat /etc/neutron/metadata_agent.ini |grep -Ev "^#|^$" | sed -e "s/^\[/\n\[/g"

[DEFAULT]
nova_metadata_ip = 172.25.250.11
metadata_proxy_shared_secret =769e58552c84467a
metadata_workers = 4
debug = False

[AGENT]

[cache]
