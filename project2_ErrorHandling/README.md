
This Ansible playbook is designed for error handling while installing Docker on Ubuntu servers

It performs the following tasks:

1. Checks if 'openssh' and 'openssl' packages are up to the latest version and ignores errors if any.
2. Checks if Docker is installed by running the 'docker --version' command and registers the result, ignoring errors.
3. Updates all packages on the system.
4. Installs 'containerd' and 'docker.io' packages if Docker is not installed.
5. Starts the Docker service if it is installed.


Execute using below command:

ansible-playbook -i inventory.ini error_handling.yml