---
title: 'Work'
date: 2018-02-10T11:52:18+07:00
heroHeading: 'What is a CNF Agent?'
heroSubHeading: ''
heroBackground: ''
---

### _Traditional VNF Programmability_
</br>
</br>

- Virtual Network Functions (VNF) offer network functions consistent with their hardware predecessors

- In clouds, they reside in virtual machines (VM)

- Orchesration, management or (SDN) controller systems deploy, program and manage VNFs - source of truth

- Planned and unplanned restarts are infrequent; accepted it will be minutes

- Up to controller systems to reconfigure VNFs upon restart

</br>
</br>


### _CNF_
</br>


- Cloud Native is microservices, containers and dynamic orchestration

- CNF = VNF packaged inside a container - as a virtual device it must be programmed accordingly. Since it resides in a CN environment it inherits its architectural and operational precepts

CNF challenges are:

- rapid spinup/spindown, no time for centralized controller to discover/configure

- lightweight, can't be burdened with management processing overhead

- multiple apps, servers, collectors to communicate with

- accomodating optimized data-plane technologies such as VPP

</br>

### CNF Agent
</br>

- Defined as software agents for the management/control of CNFs

- support data-plane programming, telemetry, logging, etc.

![cnf-agent-pict](/images/ligato-cnf-agent-pict.png)

- lightweight due to container profile

- CN environment necessities listener model where CNFs watch for config add/mod/del published by k-v stores

- extreme control channel versability as agent will talking with a multitude of different apps, services, etc. within the cluster environment

- optimized for its respective dataplane

- extensible




