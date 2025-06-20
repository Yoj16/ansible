Monitoring Stack Deployment
=========

This repository contains Ansible playbooks and roles to deploy a complete monitoring stack including Prometheus, Grafana, Loki, and Promtail.

Requirements
------------

Ansible 2.9 or higher
SSH access to target servers
Python 3.x

Installation
--------------

1. Clone this repository:
```
git clone <repository-url>
cd <repository-directory>
```

2. Configure the host inventory file: Edit the inventories/host.ini file with your server information:

```
[monitoring]
vm ansible_host=<your_server_ip> 
ansible_user=<your_ssh_user>
```

⚠️ Important: You must update the host.ini file with your specific server details before deployment.

Usage
------------

Deploy the complete monitoring stack:
```
ansible-playbook -i inventories/host.ini site.yml
```
Deploy individual components:
```
ansible-playbook -i inventories/host.ini playbooks/prometheus.yml
ansible-playbook -i inventories/host.ini playbooks/grafana.yml
ansible-playbook -i inventories/host.ini playbooks/loki.yml
ansible-playbook -i inventories/host.ini playbooks/promtails.yml
```

Components
--------
- Prometheus: Metrics collection and storage
- Grafana: Visualization and dashboarding
- Loki: Log aggregation system
- Promtail: Log shipping client for Loki

Project Structure
----------------

```
├── inventories/
│   └── host.ini         # Target inventory file (must be configured)
├── playbooks/
│   ├── grafana.yml      # Grafana deployment playbook
│   ├── loki.yml         # Loki deployment playbook
│   └── prometheus.yml   # Prometheus deployment playbook
├── roles/
│   ├── grafana/         # Grafana role
│   ├── loki/            # Loki role
│   ├── prometheus/      # Prometheus role
│   └── promtails/       # Promtail role
└── site.yml             # Main playbook
```

Access
------

- Prometheus: http://<server-ip>:9090
- Grafana: http://<server-ip>:3000 (Default login: admin/admin)
- Loki: http://<server-ip>:3100

License
-------

MIT

Contributing
-------

1. Fork the repository
2. Create your feature branch
3. Submit a pull request