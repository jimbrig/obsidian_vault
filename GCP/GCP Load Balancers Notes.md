---
creation date: 2021-05-15 15:40
modification date: Saturday 15th May 2021 15:40:04
tags: ["#note"]
author: Jimmy Briggs
---

# GCP Load Balancers Notes

## Internal HTTP Load Balancer

- regional load balancer

Requirements:

- subnets must be in the same region
  - subnet of backend managed instance group must be in the same region as the load balancer
- subnet for the backend where managed instance groups are created
- reserved subnet for proxy
  - managed by Google
  - contains the source IPs of the HTTP load balancers in that region

### Steps

1. Create a VPC, subnets and firewall rules
2. Create an instance template
3. Create a managed instance group
4. Create an internal load balancer
5. Test traffic to internal load balancer

### Firewall rules

- allow traffic from reserved subnet (load balancer subnet) to instance subnet
  - tcp: 80
- allow GCP health checks to check if managed instance group backend can be reachable
  - source IP: 130.211.0.0/22, 35.191.0.0/16
    - probe IP addresses for Internal HTTP Load Balancer
  - tcp
- allow SSH to main instance subnet
  - source IP: 0.0.0.0/0
  - tcp: 22
  
### Creating Internal HTTP(S) Load Balancer

GCP Navigation Menu > Networking Section > Network Services > Load balancing > Create Load Balancer

- Select **HTTP(S) Load Balancing**
- Internal, choose **Only between my VMs**
- Details for Name, Region, Network
- Create Reserved Subnet
- Click Create
- Backend Configuration - Create Backend Service
  - Backend type: Instance Groups
  - Choose Instance Groups
  - Create Health Check (use default)
- Routing Rules
  - Select Backend Service
  - Mode: Simple host and path rule
- Frontend Configuration
  - Protocol: HTTP
  - Choose instance subnet
  - Internal IP: Static or Ephemera
  - Port: 80
- Click Create
- Load Balancer IP is in the Frontend section

## External HTTP Load Balancing

- traffic comes from the internet

### Steps

1. Craete VPC and subnets
2. Create instance templates
3. Managed instance groups
4. Create Load Balancer

### Firewall rules

- allow GCP health checks to check if managed instance group backend can be reachable
  - source IP: 130.211.0.0/22, 35.191.0.0/16
    - probe IP addresses for Internal HTTP Load Balancer
  - tcp: 80

### Creating External HTTP(S) Load Balancer

GCP Navigation Menu > Networking Section > Network Services > Load balancing > Create Load Balancer

- Select **HTTP(S) Load Balancing**
- Internal, choose **From Internet to My VMs**
- Details for Name, Region, Network
- Create Reserved Subnet
- Click Create
- Backend Configuration - Create Backend Service
  - Backend type: Instance Groups
  - Choose Instance Groups
  - Create Health Check (use default)
- Routing Rules
  - Select Backend Service
  - Mode: Simple host and path rule
- Frontend Configuration
  - Protocol: HTTP
  - Choose instance subnet
  - Internal IP: Static or Ephemera
  - Port: 80
- Click Create
- Load Balancer IP is in the Frontend section
***
Links:  [[GCP]] | [[Google Cloud APIs]] | [[Docker]] | [[GCP Services Table]] | [[Google Cloud Setup Notes]]
Source: [Github: ivan/curada/Awesome-GCP](https://github.com/ivan-curada/Awesome-GCP)