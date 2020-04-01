[root@allinone ~(keystone_admin)]# cat /etc/glance/glance-api.conf |grep -Ev "^#|^$" | sed -e "s/^\[/\n\[/g"

[DEFAULT]
bind_host = 0.0.0.0
bind_port = 9292
workers = 4
image_cache_dir = /var/lib/glance/image-cache
registry_host = 0.0.0.0
debug = False
log_file = /var/log/glance/api.log
log_dir = /var/log/glance
rpc_backend = rabbit

[cors]

[cors.subdomain]

[database]
connection = mysql+pymysql://glance:5d6720c98e95443f@172.25.250.11/glance

[glance_store]
stores = file,http,swift
default_store = file
filesystem_store_datadir = /var/lib/glance/images/
os_region_name=RegionOne

[image_format]

[keystone_authtoken]
auth_uri = http://172.25.250.11:5000/v2.0
auth_type = password
project_name=services
username=glance
password=4dc14e758e494f20
auth_url=http://172.25.250.11:35357

[matchmaker_redis]

[oslo_concurrency]

[oslo_messaging_amqp]

[oslo_messaging_notifications]
driver =messagingv2
topics = notifications

[oslo_messaging_rabbit]
kombu_ssl_keyfile =
kombu_ssl_certfile =
kombu_ssl_ca_certs =
rabbit_host = 172.25.250.11
rabbit_port = 5672
rabbit_use_ssl = False
rabbit_userid = guest
rabbit_password = guest
default_notification_exchange = glance

[oslo_messaging_zmq]

[oslo_middleware]

[oslo_policy]
policy_file = /etc/glance/policy.json

[paste_deploy]
flavor = keystone

[profiler]

[store_type_location_strategy]

[task]

[taskflow_executor]
