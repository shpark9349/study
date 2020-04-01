[root@allinone ~(keystone_admin)]# cat /etc/keystone/keystone.conf |grep -Ev "^#|^$" | sed -e "s/^\[/\n\[/g"

[DEFAULT]
admin_token = 0ef13a083c614594a1da4a86f339753e
debug = False
log_dir = /var/log/keystone
rpc_backend = rabbit
public_port=5000
admin_bind_host=0.0.0.0
public_bind_host=0.0.0.0
admin_port=35357

[assignment]

[auth]

[cache]

[catalog]
template_file = /etc/keystone/default_catalog.templates
driver = sql

[cors]

[cors.subdomain]

[credential]
key_repository = /etc/keystone/credential-keys

[domain_config]

[endpoint_filter]

[endpoint_policy]

[eventlet_server]
public_workers=4
admin_workers=4

[federation]

[fernet_tokens]
key_repository = /etc/keystone/fernet-keys

[identity]

[identity_mapping]

[kvs]

[ldap]

[matchmaker_redis]

[memcache]

[oauth1]

[os_inherit]

[oslo_messaging_amqp]

[oslo_messaging_notifications]

[oslo_messaging_rabbit]

[oslo_messaging_zmq]

[oslo_middleware]

[paste_deploy]

[policy]

[profiler]

[resource]

[revoke]

[role]

[saml]

[security_compliance]

[shadow_users]

[signing]

[token]
expiration = 3600
provider = keystone.token.providers.uuid.Provider
driver = sql
revoke_by_id = True

[tokenless_auth]

[trust]

[ssl]
enable=False

[database]
connection=mysql+pymysql://keystone_admin:c3aa03bc905c4b0a@172.25.250.11/keystone
