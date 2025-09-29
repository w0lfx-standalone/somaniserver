# CHANGELOG

## v1.0 – Hardware & Infrastructure Planning (08/07/2025)

- Defined the overall objective: build a modular, self-hosted server environment
- Selected brand-new hardware components for virtualization and efficiency
- Planned initial architecture: Proxmox as base hypervisor, VMs for service isolation
- Outlined role of each VM (storage, services, control)
- Created the versioned documentation structure (`docs/`, `assets/`, `scripts/`)
- Initialized GitHub repository to track the full setup lifecycle

## v1.1 – Proxmox Installation and VM Setup (15/07/2025)

- Installed **Proxmox VE** on the server’s 500GB HDD as the base hypervisor  
- Configured **Linux bridge (vmbr0)** for LAN access and assigned static IP  
- Created two main VMs:  
  - **TrueNAS SCALE** – For ZFS mirror management, dataset creation, and NFS sharing  
  - **Ubuntu Server** – For running containerized services like Immich, Nextcloud, and Kasm via Docker  
- Enabled **raw device passthrough** of both 2×2TB HDDs to TrueNAS for dedicated ZFS pool  
- Allocated hardware resources:  
  - Proxmox Host – ~1.5GB RAM  
  - TrueNAS SCALE – 5.5GB RAM, 1 vCPU, 80GB boot disk  
  - Ubuntu Server – 13GB RAM, 2 vCPUs, 110GB boot disk  
- Verified boot, network access, and baseline performance of both VMs

## v1.2 – TrueNAS Setup and Pool Management (19/09/2025)
- Installed and configured TrueNAS SCALE as the storage VM  
- Created ZFS mirror pool(RAIDz1) `swimming_pool` with 2×2TB HDDs for redundancy  
- Provisioned datasets for Immich, Nextcloud, Seafile, Kasm, and Media  
- Set up NFS sharing and UID/GID mapping for consistent access from Ubuntu VM  
- Validated pool resiliency and dataset permissions

## v1.3 – Setting up Immich (29/09/2025)

- Deployed Immich on Ubuntu Server VM for private media management
- Integrated TrueNAS ZFS pool via NFS mount for persistent storage
- Configured Docker containers for Immich, PostgreSQL, and Redis
- Applied UID/GID mapping (3000:3001) across mounts for consistent access
- Enabled persistent volumes for the database and configured automated database dumps
- Implemented healthchecks and dependency conditions to ensure Immich waits for PostgreSQL & Redis before startup
- Verified file uploads, container persistence, and database backup execution
- Immich is now fully operational with redundant photo storage on the ZFS mirror
- Establishes a modular foundation for adding further services into the homelab
