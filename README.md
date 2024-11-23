# ansible-workflow-k8s
project-root/ ├── .github/ │ ├── workflows/ │ │ └── ci-cd.yml # GitHub Actions workflow for CI/CD ├── ansible/ │ ├── playbooks/ │ │ ├── deploy_cluster.yml # Provisions Kubernetes cluster │ │ ├── deploy_app.yml # Deploys the application │ │ ├── test_app.yml # Runs application tests │ │ ├── cleanup_resources.yml # Cleans up resources │ ├── roles/ │ │ ├── kubernetes_provisioning/ # Role for Kubernetes setup │ │ ├── application_deployment/ # Role for app deployment │ │ ├── cleanup/ # Role for cleanup tasks │ ├── inventory/ │ │ ├── hosts.ini # Inventory file for Ansible │ └── ansible.cfg # Ansible configuration └── README.md # Project documentation

yaml
Copy code
                   # Documentation

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
