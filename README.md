# ansible-role-cloudns-acme
ACME based LetEncrypt support using ClouDNS

This role can be plugged into the *galaxyproject.nginx* role by specifying it as the role for `nginx_ssl_role`.

It requires two variables, `acme_cloudns_auth_id` and `acme_cloudns_password`. These refer to authentication details for the
[ClouDNS API](https://www.cloudns.net/api-settings/) and as such should rely on some secure service for storage (i.e. don't
put them in plaintext in a simple file). For example this configuration snippet uses [Hashicorp Vault](https://www.vaultproject.io/)
to store these values:

```yaml
acme_cloudns_auth_id: "{{ lookup('hashi_vault', 'secret=secret/ansible/cloudns/myserver:auth_id') }}"
acme_cloudns_password: "{{ lookup('hashi_vault', 'secret=secret/ansible/cloudns/myserver:password') }}"
```
