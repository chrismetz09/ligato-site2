Notes on Design Choices

__Requirement:__ An open source solution for dynamically managing and programming VPP-based CNFs is required. 



__Solution:__ Ligato, An open source framework for building applications to control and manage VPP-based Cloud Native Network Functions (CNF).



Before delving into the "what" and "how", let's examine the "why?". In other words, why were certain design choices made for Ligato while it was being conceived, developed and tested? 

Go rather than Java or C? Protobufs vs JSON? Does Cloud Native impose constraints on traditional centralized configuration management? Why the focus on VPP in the first place? 

Understanding the "Why's" of the Ligato design will lend better insight into what it does and how it does it. Alright let's begin.

 
__1. FD.io/VPP__ 
In any network solution, it goes without saying you want THE *fastest* and most *scalable* data-plane available and FD.io/VPP fits the bill. Some highlights:   

- Performance

- Feature rich

- User Space

- Industry Mature

- open source





__2. Containerized VPP data and VPP agent__ Can run anywhere but 

3. Suite of out-of-the-box "batteries included" plugins facilitating customizable VPP data plane programmability and Upstream application interactions

4. Watch/Listener model for rapid programmability given nature of cloud native pod/container deployment frequency. KV scheduler

[etcd](https://coreos.com/etcd/)


5. written in Go. What are the reasons? Cuz things like k8s and etcd written in Go? Better performance?

RS: Go: it fits into the cloud-native world best: Docker, k8s, CNIs (as well as ETCD, but that is less important) are all in Go, so to consume their APIs, it's best to have Go infra. Also, Go apps are better performance and more lightweight than e.g. Java, while easier to code than C. 

Other Go references as source material for this section:
  
  [Go vs Java](https://www.itechart.com/blog/golang-vs-java-which-better-development/)
  
  [Doors Go Opened Blog](https://medium.com/@arschles/the-doors-go-has-opened-a4b5d0f10ea7)
  
  


6. GoVPP? so plugins can interact with VPP per doc? why are binaries used to interact with the VPP data-plane



7. why protobufs? multiple transport protocols?

Below is original notes on CNF Agent.

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