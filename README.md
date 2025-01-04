**Prerequisite:**

create ansible vault password where we would store the sensitive information

# openssl passwd sha256 2048 > myvault.pass
# ansible-vault create group_vars/all/password.yml --vault-password-file myvault.pass
<add your key: value>
save the changes and exit

If you need to change/update the vault file, then run below:

# ansible-vault edit group_vars/all/password.yml --vault-password-file myvault.pass

**This will secure any senditive information like secret keys, passwords, certificates, etc**

=============

You would also need to make passwordless ssh setup for newly created managed nodes on aws.

**Note: Port 22 must be added in security rules under security group**

Steps for passwordless authentication:
"Password Approach"

1. Login to aws instance using pem key
2. Edit /etc/ssh/sshd_config.d/<filename>.conf --> "PasswordAuthentication yes" or edit /etc/ssh/sshd_config --> remove # in front of "PasswordAuthentication yes" and add # in front of "PasswordAuthentication no"
3. systemctl restart sshd.service
4. passwd <user>
5. enter password and exit out of the instance
6. On control node,
   ssh-copy-id <user>@<publicIP of Instance>
   (One time only)Enter password
7. Now ssh to the instance. It will be passwordless setup.

=============

