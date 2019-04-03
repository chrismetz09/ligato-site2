CNF Agent explanation with figure

Traditional VNFs reside in a static environmenrt and operate in quient solitude, unencumbered by  where management/controller systems spin them up where they operate in quient solitude, unencumbered by any external drama. If they are disturbed by outside events or any unexpected illness controlled and managed

shielded from external drama protected by the thick armour of a virtual machine. 

VNFs required to be programmed with configuration. The config state

VNFs are heavyweight in  

Traditionally VNFs programmed from a centralized NMS or controller. 

Cloud Native Definition

CNF = VNF packaged inside a container - as a virtual device it must be programmed accordingly. Since it resides in a CN environment it inherits its architectural and operational precepts.

- microservices, containerized and dynamic resource placement.



subjected to the principles of CN architecture, deployment and operations.

1. have seen programmability of VNFs and virtual switches - based on programming into virtual device from a centralized controller - this means for operational (versatility, flexibility, elasticity), config held in controller - client server model, not optimal for fast deployment or restart

Motivation was to build

New model is client agent listens for and pushes info to server

place figure in img/

https://github.com/lf-edge/glossary/blob/master/edge-glossary.md#cloud-native-network-function-cnf

1. traditional VNFs operated on a client - server paradigm. 

The main motivation was that we wanted to build CNFs based on VPP. There was no management agent for VPP that could be used for that purpose - we put VPP into a container, but needed a management agent for it that would be:
fast and small footprint, since containers start and die frequently and must start within a second + they are running in multiple instances within the single host (Java - Honeycomb is a no go here)

Ondrej Fabry3/27/19, 2:43 AM
the split between vpp-agent and cn-infra is so we can have common  parts in cn-infra.. which can be generally useful in any "microservice" "agent" "cloud-native app"... and vpp-agent is like the main use for creating an agent powered by the cn-infra framework

Rastislav Szabo3/27/19, 2:44 AM
also the RPC-based management protocols (NETCONF/RESTCONF) do not fit that well for microservices, since the container can be restarted and potantially migrated to a different host, which would mean that the "controller" would need to re-discover the container IP and reprogram it after each restart - thats why we use key-value datastore for configuration, whaich allows for asynchronous configuration of microservices that may not be even runnig, and they configure themselves upon start / each restart
