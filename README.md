# Ansible Postfix role
This role is an easy way of configuring outgoing mail through a relay for local
users. It's intended to be used by local users only, for example, to send mail
from cronjobs to an external address. By default, the role uses Amazon AWS as a
relay.

An aliases file is set up along with Postfix, where all email is forwarded to
the current Ansible user. Those emails are then forwarded to an external email
address. If you need to set up a more complex aliases file, you'll need to edit
the file manually.

## Example usage in a playbook

```
- hosts: vm1.home.lan
  become: yes
  vars:
    mail_hostname: vm1.home.lan
    canonical_name: vm1.home.example.com
    external_email_address: jackbenny@example.com
    relay_host: email-smtp.eu-west-1.amazonaws.com
    relay_port: 465
    relay_user: xxx
    relay_password: yyy
    
  roles:
    - jackbenny.postfix
```
