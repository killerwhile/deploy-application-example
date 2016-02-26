


# SSH Config

In `~/.ssh/config`

```
Host pubgw1.daplab.ch
    Port 2202
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa
    ForwardAgent yes
    ProxyCommand none
    ControlPersist 60s
    ControlMaster auto
    ControlPath ~/.ssh/ssh_control_%h_%p_%r
#    User bperroud
```

# Deploying an application

```
ansible-playbook -i inventory.ini deploy-twitter-to-kafka.yml -s -e twittertokafkatesting=1
```

* `twittertokafkatesting=1` is used to download the RPM directly from [Jenkins](https://jenkins.daplab.ch), i.e. for testing :)
* The version to deploy has to be set in [roles/twitter-to-kafka/defaults/main.yml](roles/twitter-to-kafka/defaults/main.yml)
