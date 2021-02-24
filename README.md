
**This document is created for a different kind of requirement.**

 - The communication with the container and outside will be happening over Firewall
(Cisco vASA).
 - To monitor traffic over a firewall.
 - Control the access with firewall rules.

### Docker

Docker is a computer program that performs operating-system-level virtualization also known as containerization. It was first released in 2013 and is developed by Docker, Inc. Docker is used to run software packages called "containers".

### Container

A container image is a lightweight, stand-alone, executable package of a piece of software that includes everything needed to run it: code, runtime, system tools, system libraries, settings.


### Docker Swarm

Docker Swarm is native clustering for Docker. It turns a pool of Docker hosts into a single, virtual Docker host. Because Docker Swarm serves the standard Docker API, any tool that already communicates with a Docker daemon can use Swarm to transparently scale to multiple hosts.

## Swarm Contiv Cluster Architecture:


1. Cluster setup with 3 master nodes and 3 worker nodes.
2. All the node will be having 2 networker Interface. 1 management interface with 11.11.x.x networker and other contive network interface.(You can select the subnet as per your infra setup).
3. 1 Cisco vASA firewall(v981 or v991). I have worked on 981.


![D-S-Contiv](https://github.com/bishnuroy/Docker-Swarm-Contiv/blob/master/Image/D-S-Contiv.png)


 
