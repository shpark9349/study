[root@allinone ~(keystone_admin)]# cat /etc/neutron/neutron.conf |grep -Ev "^#|^$" | sed -e "s/^\[/\n\[/g" 

[DEFAULT]
bind_host=0.0.0.0
auth_strategy=keystone
core_plugin=neutron.plugins.ml2.plugin.Ml2Plugin
service_plugins=neutron_lbaas.services.loadbalancer.plugin.LoadBalancerPluginv2,router,metering
allow_overlapping_ips=True
notify_nova_on_port_status_changes=True
notify_nova_on_port_data_changes=True
api_workers=4
rpc_workers=4
router_scheduler_driver=neutron.scheduler.l3_agent_scheduler.ChanceScheduler
l3_ha=False
max_l3_agents_per_router=3
debug=False
log_dir=/var/log/neutron
rpc_backend=rabbit
control_exchange=neutron
nova_url=http://172.25.250.11:8774/v2

[agent]
root_helper=sudo neutron-rootwrap /etc/neutron/rootwrap.conf

[cors]

[cors.subdomain]

[database]
connection=mysql+pymysql://neutron:b8970e00d4a7448e@172.25.250.11/neutron

[keystone_authtoken]
auth_uri=http://172.25.250.11:5000/v2.0
auth_type=password
project_name=services
password=7857c0a9df1a49c8
username=neutron
project_domain_name=Default
user_domain_name=Default
auth_url=http://172.25.250.11:35357

[matchmaker_redis]

[nova]
region_name=RegionOne
auth_url=http://172.25.250.11:35357
auth_type=password
password=9962d427bbd648a2
project_domain_id=default
project_name=services
tenant_name=services
user_domain_id=default
username=nova

[oslo_concurrency]
lock_path=$state_path/lock

[oslo_messaging_amqp]

[oslo_messaging_notifications]

[oslo_messaging_rabbit]
kombu_ssl_keyfile=
kombu_ssl_certfile=
kombu_ssl_ca_certs=
rabbit_host=172.25.250.11
rabbit_port=5672
rabbit_use_ssl=False
rabbit_userid=guest
rabbit_password=guest

[oslo_messaging_zmq]

[oslo_middleware]

[oslo_policy]
policy_file=/etc/neutron/policy.json

[qos]

[quotas]

[ssl]

[service_providers]
service_provider=LOADBALANCERV2:Haproxy:neutron_lbaas.drivers.haproxy.plugin_driver.HaproxyOnHostPluginDriver:default
