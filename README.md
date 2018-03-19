sbog/letsencrypt
================

Role to help issue LetsEncrypt certificate

#### Requirements

Ansible 2.4

#### Role Variables

```yaml
## Common settings
# available acme tools: certbot, dehydrated, acme.sh
le_acme_tool: acme.sh
# LE email
le_email: admin@localhost.com
# hostname to issue cert for. Required to set if domain_names not used
le_hostname: ""
# domain names to issue cert for. Overrides le_hostname. Required to set
# if le_hostname not used
le_domain_names: []
# challenge type: webroot, standalone, nginx, dns
le_challenge: dns
## Acme.sh settings
# webroot path
acme_sh_webroot_path: /var/www/webroot
# type of supported dns api (used only if dns challenge used)
acme_sh_dns_type: dns_gd
# vars which need to be exported in case of dns api usage
# about naming look at https://github.com/Neilpang/acme.sh/tree/master/dnsapi
acme_sh_dns_vars:
  GD_Key: somekeyshouldbehere
  GD_Secret: secretshouldbehere
##
dns_holder: bind
aws_access_key_id: False
aws_secret_access_key: False
dh_challenge: "dns-01"
dh_basedir: /etc/ssl_certs
```

#### Dependencies

None

#### Example Playbook

```yaml
- name: Issue needed Let's Encrypt certificate
  hosts: letsencrypt
  remote_user: root

  roles:
    - letsencrypt
```

#### License

Apache 2.0

#### Author Information

Stanislaw Bogatkin (https://sbog.ru)
