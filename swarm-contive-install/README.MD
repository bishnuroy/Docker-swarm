
I followed following document fo install swarm contive cluster.

https://github.com/contiv/install

### Step 1:

Download contive ansible cluster setup "https://github.com/contiv/install/releases" from this url.
      
```
# wget https://github.com/contiv/install/releases/download/1.1.9/contiv-full-1.1.9.tgz
```

### Step 2:

Extract the file 
      
```
tar -zxvf contiv-full-1.1.9.tgz 
```
    
### Step 3:

go to contiv-"version" folder

```
cd contiv-1.1.9/

[root@xxx contiv-1.1.9]# ls
ansible  contiv_cache  install  README.md
[root@xxx contiv-1.1.9]#

```
### Step 4:

Now edit "install/ansible/cfg.yml" file with fillowing details.


```consile
CONNECTION_INFO:
  master-node1-management-ip:
        role: master
        control: eth1
        data: eth2
  master-node2-management-ip:
        role: master
        control: eth1
        data: eth2
  master-node3-management-ip:
        role: master
        control: eth1
        data: eth2
  worker-node1-management-ip:
        control: eth1
        data: eth2
  worker-node3-management-ip:
        control: eth1
        data: eth2
  worker-node3-management-ip:
        control: eth1
        data: eth2
```

### Step 5:

Now execute below command to setup the cluster.

Enabled key based authentication in between execution server and cluster servers.

```
./install/ansible/install_swarm.sh -f cfg.yml -e <ssh key> -u <username> -i
```

