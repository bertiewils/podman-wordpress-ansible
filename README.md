# podman-wordpress-ansible

An example playbook to deploy WordPress, NGINX and a MySQL DB in containers, utilising Podman.

Project requirements:

- Install Podman
- Create a podman user
- Deploy WordPress and NGINX in front
- Data must persist


Notes:

- Persistent data resides in `/opt/wordpress`
- The three containers run within a pod
- For simplicity sensitive variables have been included in plain text
- Default variables can be found in the relevant defaults/main.yml file. Override them in group_vars/webserver/main.yml
- For simplicity I opted for a firewall redirect from 80 -> 8080 instead of lowering the net.ipv4.ip_unprivileged_port_start

Tested on Rocky Linux 8.5.

## Usage

Install requirements with:

```
ansible-galaxy install -r requirements.yml
```

Then run with:

```
ansible-playbook deploy.yml
```

Once completed, visit [http://hostname_or_IP_address/wp-admin](http://hostname_or_IP_address/wp-admin) to continue setup.
