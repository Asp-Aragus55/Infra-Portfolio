# Data Platform Modernization (In Progress)

## Overview
Leading a transformation of legacy file server architecture into a purpose-built data platform, aligning storage solutions with specific workloads (collaboration, project data, models, and archival).

## Problem
- Monolithic file server (shares/folders) used for all workloads  
- No separation between:
  - collaboration data  
  - project data  
  - large model files  
  - archival storage  
- Poor performance and scalability  
- Difficult to manage permissions and data lifecycle  
- On-prem SAN reached capacity limits  
- Replacement cost increased significantly (~$250K → ~$700K), making traditional expansion cost-prohibitive  
- Required a strategic shift away from centralized on-prem storage   

## Constraints
- Existing data actively in use across multiple teams  
- No downtime allowed during transition  
- Required to maintain access to legacy data during migration  
- Multiple platforms required for different workloads  
- Cost considerations for long-term storage (archive strategy)  

## Decision
Redesigned data architecture to separate workloads into appropriate platforms, driven by both scalability needs and cost constraints of expanding on-prem storage:
- Collaboration → SharePoint  
- Project data → Egnyte  
- Models → Autodesk Construction Cloud (Forma)  
- Archives → NAS (short-term), planning transition to Azure Blob Storage  

## Architecture
```
Users
 ↓
Collaboration → SharePoint
Project Data → Egnyte
Models → ACC (Forma)
Archive → NAS → (planned) Azure Blob Storage
```

## Implementation (In Progress)
- Defined data classification and target platforms  
- Migrating collaboration data to SharePoint  
- Transitioning project data to Egnyte  
- Moving model workflows to ACC (Forma)  
- Maintaining archive data on NAS during transition  
- Planning Azure Blob Storage strategy for long-term archival  

## Challenges
- Data classification across inconsistent legacy structure  
- Ensuring continuity of access during migration  
- Aligning user workflows to new platforms  
- Managing multiple systems with different access models  
- Estimating and optimizing cloud storage costs for archival data  

## Outcome (Current State)
- Clear separation of data by function  
- Improved collaboration workflows  
- Reduced reliance on monolithic file server  
- Established foundation for scalable, cloud-aligned data strategy  

## Next Steps
- Finalize Azure Blob Storage architecture for archives  
- Complete migration of remaining legacy data  
- Optimize cost and lifecycle policies for long-term storage  

## Takeaway
Separating data by workload rather than storing everything in a single file system significantly improves scalability, usability, and long-term maintainability.
