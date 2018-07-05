Follow this document to install docker service.


https://docs.docker.com/install/linux/docker-ce/centos/

## Dependency service:

If needed install them by following below commands.

### container-selinux-2.9

```
yum install ftp://ftp.icm.edu.pl/vol/rzm3/linux-centos-vault/7.3.1611/extras/x86_64/Packages/container-selinux-2.9-4.el7.noarch.rpm
```

### pigz

```
yum install ftp://ftp.icm.edu.pl/vol/rzm6/linux-oracle-repo/OracleLinux/OL7/developer_EPEL/x86_64/pigz-2.3.4-1.el7.x86_64.rpm
```

Copy server.pem, server-key.pem, client.pem, client-key.pem, ca.crt file in "/etc/docker/certs/" folder.

Edit docker service file like below to enable tls.

## Docker Service without tls:

### cat /usr/lib/systemd/system/docker.service

```console
[Unit]
Description=Docker Application Container Engine
Documentation=https://docs.docker.com
After=network.target

[Service]
TimeoutStartSec=5m
Type=notify
ExecStart=/usr/bin/dockerd  -H tcp://0.0.0.0:2385 -H unix:///var/run/docker.sock --cluster-store=etcd://localhost:2379
MountFlags=shared
LimitNOFILE=1048576
LimitNPROC=1048576
LimitCORE=infinity

[Install]
WantedBy=multi-user.target
```

## Docker Service with tls:


### cat /usr/lib/systemd/system/docker.service

```console
[Unit]
Description=Docker Application Container Engine
Documentation=https://docs.docker.com
After=network.target

[Service]
TimeoutStartSec=5m
Type=notify


ExecStart=/usr/bin/dockerd  --tlsverify --tlscacert=/etc/docker/certs/ca.pem --tlscert=/etc/docker/certs/server.pem --tlskey=/etc/docker/certs/server-key.pem -H tcp://0.0.0.0:2376 -H unix:///var/run/docker.sock --cluster-store=etcd://localhost:2379
MountFlags=shared
LimitNOFILE=1048576
LimitNPROC=1048576
LimitCORE=infinity

[Install]
WantedBy=multi-user.target
```

Restart the docker service.
