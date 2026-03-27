# Hybrid Identity → Entra SSO Rollout

## Overview
Established Microsoft Entra ID as the primary identity provider in a hybrid AD environment, enabling SSO across core applications while maintaining compatibility with legacy systems.

## Problem
- Authentication was fragmented across applications  
- No centralized identity control  
- Increasing administrative overhead  
- Inconsistent user login experience  

## Constraints
- Hybrid AD environment (on-prem still required)  
- No safe testing path for desktop application authentication (O365, Autodesk)  
- Some services required federation and could not be migrated immediately  
- Certain changes required tenant-wide enforcement  
- Needed to avoid user disruption during rollout  

## Decision
Moved toward Entra as the central identity provider using a phased rollout approach, prioritizing applications with native SSO support and deferring federation-dependent systems.

## Implementation
- Configured Entra as primary IdP  
- Integrated SSO for:
  - Microsoft 365  
  - Autodesk  
  - Bluebeam  
- Created a test group for staged rollout  
- Identified and deferred federation-dependent services  
- Implemented Conditional Access policies  
- Validated authentication behavior across hybrid environment  

## Challenges
- No isolated test environment for desktop authentication flows  
- Tenant-wide impact required for certain integrations  
- Hybrid identity inconsistencies during rollout  
- Limited ability to fully validate behavior before enforcement  

## Outcome
- Centralized authentication across core systems  
- Reduced login friction for users  
- Improved security posture via Conditional Access  
- Established foundation for Zero Trust model  

## Takeaway
Identity changes in hybrid environments have broad impact; phased rollout and constraint-driven decisions were required to avoid disruption while progressing toward a modern identity model.
