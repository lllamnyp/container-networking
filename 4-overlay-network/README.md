# Overlay Network

An example of creating multiple L2 networks, one on each of the nodes. Each network contains
2 network namespaces (containers), connected via a bridge, and have different subnets. The 
containers are connected via an overlay network implemented with a tuntap device and a UDP
cnnection between hosts.

![Diagram](./diagram.jpg)

Create the 2 VMs (container-networking-1 and container-networking-2):

```
vagrant up
```

SSH to each node (VM) in turn, and run the setup script to create the network namespaces connected via a bridge: 

```
vagrant ssh 4-overlay-network-[12]
./setup.sh
```

To test the connectivity between the containers within and node, and across nodes, run the following:

```
./test.sh
```

To teardown the network:

```
./teardown.sh
```

To test the entire flow, i.e. setup - run the tests - teardown, from your machine, run the following:

```
make
```
