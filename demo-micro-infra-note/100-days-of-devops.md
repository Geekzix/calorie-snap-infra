# 100 Days of Devops

- [Learning Resources](#learning-resources)

## Learning Resources
- [Eight ways to protect SSH access on your system](https://www.redhat.com/en/blog/eight-ways-secure-ssh)

## Linux Server Config

1. Disable direct root ssh login

- login to remote server
    ```
    ssh <username>@<server-addr>
    ```
- config `PermitRootLogin no` in sshd_config 
    ```
    sudo vim /etc/ssh/sshd_config
    ```
- Restart sshd service
    ```
    sudo systemctl restart sshd
    ```
- Check config
    ```
    sudo sshd -T | grep permitrootlogin
    ```

