# VPN Replacement with Entra Global Secure Access

## Overview
Replaced traditional VPN-based remote access with Microsoft Entra Global Secure Access (Private Access), enabling secure, identity-based connectivity to internal resources without reliance on VPN infrastructure.

## Problem
- VPN reliability issues and inconsistent user experience  
- Dependency on network-level access for resource connectivity  
- Increased support overhead for remote access issues  
- Limited alignment with Zero Trust principles  

## Constraints
- Existing environment relied on SMB shares and internal resources  
- Required continued access to on-prem systems during transition  
- Needed to maintain user access without disruption  
- Hybrid identity environment (on-prem AD + Entra)  
- No fallback to legacy VPN model during testing  

## Decision
Implemented Entra Global Secure Access (Private Access) to shift from network-based access to identity-driven access, removing dependency on traditional VPN while maintaining access to required internal services.

## Architecture
```
User Device → GSA Client
               ↓
        Entra Authentication
               ↓
     Private Access Connector
               ↓
     Internal Resources (SMB, Apps)
```

## Implementation
- Configured Global Secure Access baseline (Quick Access)  
- Deployed Private Access connectors for internal resource access  
- Defined access policies for internal services (SMB, applications)  
- Configured DNS and routing for internal resource resolution  
- Transitioned users from VPN to GSA access model  
- Validated connectivity to internal resources over GSA  

## Challenges
- SMB connectivity inconsistencies over GSA  
- DNS resolution issues (suffix conflicts, internal vs external resolution)  
- Overlapping access policies between test and production groups  
- Difficulty isolating behavior due to hybrid environment  
- Lack of clear testing boundary before full enforcement  

## Outcome
- Eliminated dependency on traditional VPN  
- Improved remote access experience for users  
- Reduced support overhead for connectivity issues  
- Established identity-based access model aligned with Zero Trust principles  

## Takeaway
Replacing VPN with identity-driven access introduces new complexities (especially around DNS and SMB), but significantly improves long-term scalability and security when properly implemented.
