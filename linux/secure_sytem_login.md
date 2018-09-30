# Secure the system with ssh login

Any newly installed OS needs to go through the following to secure for securing from malicious login attacks.
1. SSH login as root is enabled
2. Password authentication is enabled
3. New user/Existing user has a password
4. SSH service is running on 22

To Secure do the following
- Disable root login first. Edit `/etc/ssh/sshd_config` and update the following parameters
```shell
Port <a port number other than 22>
PermitRootLogin no # This will disable ssh login as root i.e., root@<server ip>
PasswordAuthentication no # To disable tunneled clear text passwords, change to no here!
ChallengeResponseAuthentication no
UsePAM no
```
- Restart ssh daemon
```
service ssh restart
```
- Now attempt `ssh root@<server ip>` and you should get the following std out
```
root@<server ip> Permission denied (publickey).
```