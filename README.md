`
clone 到python可搜索的路径下，如：/usr/local/lib/python3.6/site-packages/
`


Configuration
=============

Activate authentication via this LDAP backend in `airflow.cfg` config:

```
[webserver]
authenticate = True
auth_backend = airflow-alt-ldap.auth.backend.ldap_auth
```

Then you can configure that module using the following keys (example conf to be adapted):
```
uri = ldap://localhost:389
user_basedn = ou=people,dc=xx,dc=com
user_filter = cn=*
user_name_attr = cn
group_basedn = ou=group,dc=xx,dc=com
group_member_attr = member
group_filter = cn=*
superuser_filter = cn=admin
data_profiler_filter = cn=rd
bind_user = uid=binddn,dc=example,dc=com
bind_password = MyAwesomePassword
# cacert = /etc/ca/ldap_ca.crt
# Set search_scope to one of them: BASE, LEVEL , SUBTREE
# Set search_scope to SUBTREE if using Active Directory, and not specifying an Organizational Unit
search_scope = SUBTREE

```