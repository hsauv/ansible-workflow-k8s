# ansible-workflow-k8s
project-root/
├── .github/
│   ├── workflows/
│   │   └── ci-cd.yml  # Your GitHub Actions workflow
├── ansible/
│   ├── playbooks/
│   │   ├── deploy_cluster.yml       # Provisions your Kubernetes cluster
│   │   ├── deploy_app.yml           # Deploys your application
│   │   ├── test_app.yml             # Runs tests against your application
│   │   ├── cleanup_resources.yml    # Cleans up cluster resources
│   ├── roles/
│   │   ├── kubernetes_provisioning/ # Role for setting up Kubernetes
│   │   ├── application_deployment/ # Role for app deployment
│   │   ├── cleanup/                # Role for cleaning up resources
│   ├── inventory/
│   │   ├── hosts.ini                # Inventory file for target nodes
│   └── ansible.cfg                  # Ansible configuration
└── README.md                        # Documentation

Key Components
1. Playbooks (ansible/playbooks/)

Playbooks are the main scripts that define your CI/CD tasks.

Examples:
deploy_cluster.yml: Sets up your Kubernetes cluster.
deploy_app.yml: Deploys your application.
test_app.yml: Runs application tests.
cleanup_resources.yml: Cleans up resources after testing.

2. Roles (ansible/roles/)
Roles group related tasks into reusable components.

Examples:
kubernetes_provisioning: Handles Kubernetes cluster setup.
application_deployment: Manages application deployment tasks.
cleanup: Removes CRDs, namespaces, and other resources.

3. Inventory (ansible/inventory/)
Defines the target nodes or environments for your tasks.

Example: hosts.ini
ini

[k8s_nodes]
192.168.1.10 ansible_user=ubuntu

[registry]
192.168.1.20 ansible_user=ubuntu
4. Ansible Configuration (ansible/ansible.cfg)
Central configuration for Ansible behavior.
Example:
ini

[defaults]
inventory = ./inventory/hosts.ini
roles_path = ./roles
host_key_checking = False
