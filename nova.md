[DEFAULT]
auth_strategy=keystone
use_forwarded_for=False
fping_path=/usr/sbin/fping
instance_usage_audit_period=hour
rootwrap_config=/etc/nova/rootwrap.conf
allow_resize_to_same_host=False
reserved_host_memory_mb=512
instance_usage_audit=True
heal_instance_info_cache_interval=60
default_floating_pool=public
force_snat_range=0.0.0.0/0
metadata_host=172.25.250.11
dhcp_domain=novalocal
use_neutron=True
notify_on_state_change=vm_and_task_state
notify_api_faults=False
ssl_only=True
cert=/etc/pki/tls/certs/ssl_vnc.crt
key=/etc/pki/tls/private/ssl_vnc.key
state_path=/var/lib/nova
scheduler_host_subset_size=1
scheduler_use_baremetal_filters=False
scheduler_available_filters=nova.scheduler.filters.all_filters
scheduler_default_filters=RetryFilter,AvailabilityZoneFilter,RamFilter,DiskFilter,ComputeFilter,ComputeCapabilitiesFilter,ImagePropertiesFilter,ServerGroupAntiAffinityFilter,ServerGroupAffinityFilter,CoreFilter
scheduler_weight_classes=nova.scheduler.weights.all_weighers
scheduler_host_manager=host_manager
scheduler_driver=filter_scheduler
max_io_ops_per_host=8
max_instances_per_host=50
scheduler_max_attempts=3
report_interval=10
enabled_apis=osapi_compute,metadata
osapi_compute_listen=0.0.0.0
osapi_compute_listen_port=8774
osapi_compute_workers=4
metadata_listen=0.0.0.0
metadata_listen_port=8775
metadata_workers=4
compute_manager=nova.compute.manager.ComputeManager
service_down_time=60
compute_driver=libvirt.LibvirtDriver
vif_plugging_is_fatal=True
vif_plugging_timeout=300
firewall_driver=nova.virt.firewall.NoopFirewallDriver
force_raw_images=True
debug=False
log_dir=/var/log/nova
rpc_backend=rabbit
image_service=nova.image.glance.GlanceImageService
osapi_volume_listen=0.0.0.0
volume_api_class=nova.volume.cinder.API
image_cache_manager_interval = 60
disk_allocation_ratio = 8.0
cpu_allocation_ratio = 8.0
ram_allocation_ratio = 8.0

[api_database]
connection=mysql+pymysql://nova_api:a4975fb0e170478a@172.25.250.11/nova_api

[barbican]

[cache]

[cells]

[cinder]
catalog_info=volumev2:cinderv2:publicURL

[cloudpipe]

[conductor]
workers=4

[cors]

[cors.subdomain]

[crypto]

[database]
connection=mysql+pymysql://nova:a4975fb0e170478a@172.25.250.11/nova

[ephemeral_storage_encryption]

[glance]
api_servers=172.25.250.11:9292

[guestfs]

[hyperv]

[image_file_url]

[ironic]

[key_manager]

[keystone_authtoken]
auth_uri=http://172.25.250.11:5000/v2.0
auth_type=password
username=nova
project_name=services
auth_url=http://172.25.250.11:35357
password=9962d427bbd648a2

[libvirt]
virt_type=kvm
inject_password=False
inject_key=False
inject_partition=-1
live_migration_uri=qemu+tcp://nova@%s/system
cpu_mode=none
vif_driver=nova.virt.libvirt.vif.LibvirtGenericVIFDriver

[matchmaker_redis]

[metrics]

[mks]

[neutron]
url=http://172.25.250.11:9696
region_name=RegionOne
ovs_bridge=br-int
extension_sync_interval=600
service_metadata_proxy=True
metadata_proxy_shared_secret=769e58552c84467a
timeout=60
auth_type=v3password
auth_url=http://172.25.250.11:35357/v3
project_name=services
project_domain_name=Default
username=neutron
user_domain_name=Default
password=7857c0a9df1a49c8

[osapi_v21]

[oslo_concurrency]
lock_path=/var/lib/nova/tmp

[oslo_messaging_amqp]

[oslo_messaging_notifications]
driver=messagingv2

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
policy_file=/etc/nova/policy.json

[placement]

[placement_database]

[rdp]

[remote_debug]

[serial_console]

[spice]

[ssl]

[trusted_computing]

[upgrade_levels]

[vmware]

[vnc]
enabled=True
keymap=en-us
vncserver_listen=0.0.0.0
vncserver_proxyclient_address=allinone.lab.example.com
novncproxy_base_url=https://172.25.250.11:6080/vnc_auto.html
novncproxy_host=0.0.0.0
novncproxy_port=6080

[workarounds]

[wsgi]
api_paste_config=api-paste.ini

[xenserver]

[xvp]
