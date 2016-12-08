# Docker-swarm

Docker swarm manager setup (3 nodes)
Services running on YKT Vms

    k8smaster.00.com
        Docker v1.12
        etcd v2.3.1
        Swarm manager v1.2.0
        contiv netmaster v0.1-07-14-2016.07-06-17.UTC
        contiv netplugin v0.1-07-14-2016.07-06-17.UTC

    for service in docker etcd swarm netmaster netplugin; do systemctl start $service; systemctl status $service; done

    k8sminion1.00.com
        Docker v1.12
        etcd v2.3.1
        Swarm manager v1.2.0
        contiv netplugin v0.1-07-14-2016.07-06-17.UTC

    for service in docker etcd swarm netplugin; do systemctl start $service; systemctl status $service; done

    k8sminion2.00.com
        Docker v1.12
        etcd v2.3.1
        Swarm manager v1.2.0
        contiv netplugin v0.1-07-14-2016.07-06-17.UTC

    for service in docker etcd swarm netplugin; do systemctl start $service; systemctl status $service; done

