setup-alertmanager
=========

This role will instantiate a alertmanager container on targeted hosts. The notifications are sent to SMTP port (25) on the host server.

Requirements
------------

Docker must be available and running on the targeted hosts.

Role Variables
--------------
Default values of variables:
```
alertmanager_image: 'prom/alertmanager'
alertmanager_image_version: 'latest'
alertmanager_port: '9093'

provision_state: "started"

smtp_host: my_smtp_host
smtp_port: my_smtp_port
from: my_smtp_from
smtp_username: 'smtp_user'
smtp_password: 'smtp_password'
notification_recipients: recipients@example.com

```
`alertmanager_image` - The alertmanager image to deploy. <br />
`alertmanager_image_version` - The image tag to deploy. <br />
`alertmanager_port` - The port to expose on the target hosts. <br />
`provision_state` - Options: [absent, killed, present, reloaded, restarted, **started** (default), stopped] <br />

`smtp_host:` -  smtp server to which the notifications are send <br />
`smtp_port:` - smtp port <br />
`from:` -  sender <br />
`smtp_username:` -  smtp server password <br />
`smtp_password:` -  smtp server password <br />
`notification_recipients:` - email address of the recipients <br />


Dependencies
------------
```
python >= 2.6
docker-py >= 0.3.0
The docker server >= 0.10.0
```

Example Playbook
----------------
```
- name: Setup alertmanager
  hosts: prometheus_master
  become: True
  vars:
    provision_state: "started"
  roles:
    - prometheus/generic/setup-alertmanager
```

License
-------

BSD
