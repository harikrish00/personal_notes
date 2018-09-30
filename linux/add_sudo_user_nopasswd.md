# Adding a new sudo user with nopassword
Platform: Debian

- Create a user using the following command, and provide password
```
adduser --home /home/<user> --shell /bin/bash <user>
```

- Modify the user to make it a sudo user
```
usermod -aG sudo <user>
```

- Now the user can do `sudo <command>` but, it will prompt for the password
- In order to make it nopassword sudo login, drop a file under `/etc/sudoers.d`
One can directly edit the `/etc/sudoers` but it might be cleared during system update.
- Sudoers file has a directive at the end `#includedir /etc/sudoers.d` which takes care of including all the files under the directory
- Create a new file under sudoers.d Ex. `<user>-nopasswd` 
- NOTE: You can not edit the newly created file since the permissions are not to edit directly.
- Use `visudo -f <filename>` to edit. And paste the following line in there
```
user ALL=(ALL) NOPASSWD: ALL
```


> useradd is native binary compiled with the system. But, adduser is a perl script which uses useradd binary in back-end.
> adduser is more user friendly and interactive than its back-end  useradd. There's no difference in features provided.