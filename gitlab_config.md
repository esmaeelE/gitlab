# Append these lines to gitlab.rb

```
external_url 'https://dev-gitlab.example.com'
nginx['listen_addresses'] = ['127.0.0.1']
nginx['listen_port'] = 8888
nginx['listen_https'] = false

# Not work in nginx proxy manager if i use gitlab domain
# registry_external_url 'https://gitlab.example.com:5050'

registry_external_url 'https://registry-gitlab.example.com'
registry_nginx['listen_addresses'] = ['127.0.0.1']
registry_nginx['listen_port'] = 9999
registry_nginx['listen_https'] = false


# LDAP SERVER
gitlab_rails['ldap_enabled'] = true                                                                                                                           
gitlab_rails['prevent_ldap_sign_in'] = false                                                                                                                  

gitlab_rails['ldap_servers'] = YAML.load <<-'EOS'                                                                                                              
  main:                                                                                                                                                        
    label: 'My LDAP'                                                                                                                                           
    host: '1.2.3.4'                                                                                                                                       
    port: 389
    uid: 'cn'
    bind_dn: 'cn=admin,dc=example,dc=com'
    password: 'S3cr3tP@$$word'
    timeout: 10
    encryption: 'start_tls'
    verify_certificates: false
    smartcard_auth: false
    active_directory: false
    allow_username_or_email_login: false
    lowercase_usernames: false
    block_auto_created_users: false
    base: 'dc=example,dc=com'
EOS

```
