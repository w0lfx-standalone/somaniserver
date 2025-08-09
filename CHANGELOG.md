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
