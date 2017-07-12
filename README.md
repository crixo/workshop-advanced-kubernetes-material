# KubePrimer Workshop

Welcome to the KubePrimer workshop repository. This workshop is organized by [SIGHUP](http://sighup.io), the aim is to introduce all the participants to the basics concepts behind [Kubernetes](http://kubernetes.io).

## Preparation & Setup

You will need to have a laptop (Windows, Linux or Mac), it is preferred for your machine to have at least 8GB of RAM. This isn't strictly required but highly recommended. Working with VMs and Containers **is** resource intensive, no way to get around it.

This workshop requires that you have the following installed on your machine:
- [Virtualbox](https://www.virtualbox.org/)
- [Vagrant](https://www.vagrantup.com/downloads.html)
- [Minikube](https://github.com/kubernetes/minikube#installation)

In order to speed up the setup process, we also recommend you to download the VMs & containers required during the workshop.

### Downloading vagrant box

Start downloading the vagrant box. This isn't strictly required but again, recommended for you to test the multi-node scenario. You can do that with the following command `vagrant box add bento/ubuntu-16.04`

### Setting up minikube

Minikube is a simple one-node installation of Kubernetes specifically designed to work on your local machine.

Do the following commands to setup the minikube installation:

1. `minikube start`, this will setup the minikube VM
2. `minikube ssh` to get into the machine
3. From inside the machine do `docker pull sighup/kubeprimer-web`, `docker pull sighup/kubeprimer-backend`, `docker pull mongo:3.0.15`

If you don't know what those commands are for or how they work specifically, do not worry. We will review them during the workshop.

