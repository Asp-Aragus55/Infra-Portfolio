# Network Infrastructure Redesign

## Overview
Led a full redesign of a legacy network environment to improve stability, segmentation, and resilience, coordinating with external contractors for implementation while owning architecture and delivery.

## Problem
- Flat /8 network (192.168.x.x) with no segmentation  
- Frequent connection drops and instability  
- Failing edge switch stack causing random outages  
- Firewalls not configured for high availability  
- No ISP failover  
- DNS inconsistencies across environment  
- No foundation for Zero Trust or network-level isolation  

## Constraints
- Existing infrastructure had to remain operational during transition  
- Limited tolerance for downtime  
- Hardware limitations required reuse of some existing components  
- Needed to improve stability without introducing unnecessary complexity  

## Decision
Redesigned the network into a segmented, fault-tolerant architecture using VLAN separation, proper IP scoping (10.x.x.x /24), and firewall high availability, while simplifying unstable components.

## Architecture
```
Clients → VLAN (User Network)
Servers → VLAN (Server Network)
Voice → VLAN (Voice Network)
VPN → VLAN (Remote Access)

           ↓
      Core Switching Layer
           ↓
   HA Firewalls (SonicWall)
           ↓
     Primary ISP / Failover ISP
```

## Implementation
- Defined network segmentation strategy and IP scheme (10.x.x.x /24)  
- Designed VLAN structure (user, server, voice, VPN traffic)  
- Directed contractor implementation for switch and firewall configuration  
- Oversaw conversion of firewalls to HA configuration (active/passive)  
- Coordinated implementation of secondary ISP for failover  
- Managed physical reorganization and rewiring of network stack  
- Standardized DNS configuration across environment  
- Executed changes in phased rollout with testing prior to user impact  

## Challenges
- Maintaining uptime during network transition  
- Diagnosing instability caused by failing switch stack  
- Coordinating contractor execution with internal requirements  
- Readdressing network without breaking existing services  
- Cleaning up inconsistent DNS behavior across systems  

## Outcome
- Eliminated recurring network instability and random drops  
- Improved network performance and reliability  
- Established proper traffic segmentation  
- Introduced failover capability for internet connectivity  
- Created foundation for Zero Trust and future cloud integration  

## Takeaway
Effective infrastructure redesign requires both architectural ownership and coordinated execution; clear direction and phased rollout were critical to stabilizing a previously unreliable environment.
