# Virtual Private Cloud VPC
Your VPC networks connect
your Google Cloud platform resources to each other and to the internet
The Virtual Private Cloud networks that you define have global scope.
They can have subnets in any GCP region
worldwide and subnets can span the zones that make up a region.
This architecture makes it easy for you to
define your own network layout with global scope

You can dynamically increase the size of a subnet in
a custom network by expanding the range of IP addresses allocated to it. Doing that doesn't affect already configured VMs

![](images/vpc.png?raw=true)

# Compute Engine
Lets you create and run virtual machines, these are some details:
- Pick a machine type which orR make a custom one
- Persistent storage: standard or SSD
- Local SSDs: high-performance scractch space; doesn't last past when the VM terminates
- Boot images: pre-defined or custom by you
- Startup script
- Snapshots
- Preemtible vm: gives compute engine permisions to terminate if its resources are needed elsewher down once is not working

auto-scaling

# Important VPC capabilities

Are used to forward traffic from one instance to another within the same network. Even across sub-networks or
even between GCP zones without requiring an external IP address.
- Routing tables are built in you don't have to manage a router.
- Global distributed firewall: can define rules in terms of metadata tags on Compute Engine
instances (really convenient).IE: can tag all your web servers with "web", write a firewall rule saying: traffic
on ports 80 or 443 is allowed into all VMs with the "web" tag, no matter the IP address. 
- VPC Peering: stablishes peering relationship between two VPCs so that they can exchange traffic
- Shared VPC: use IAM to control who and what in one project can interact with a VPC in another
- Cloud Load Balancing: fully distributed, software-defined managed service for all your traffic. You
don't have to worry about scaling or managing them.
  - HTTPS load balancing: for cross regional load balancing for a web application
  - Global SSL proxy load balancer: for SSL non-HTTP traffic (only TCP)
  - TCP proxy load balancer: non-SSL TCP traffic (only TCP)
  - Regional load balancer: load balance UDP traffic or traffic on any port number, across a GCP region
  - Internal load balancer: load balance traffic inside your project
- Cloud DNS: managed DNS service running on the same infrastructure as Google, also programmable
- Cloud CDN: uses google's globally distributed edge caches to cache content close to your users
- Cloud Router: lets your other networks and your Google VPC exchange route information over the VPN
using the Border Gateway Protocol
- Direct Peering: private connection between you and Google for hybrid cloud workloads it isn't covered by a Google service level agreement.
