# Azure-Fundamentals-Hands-On-Capstone-ProjectOverview
Overview

Nimbus Compute is a hands-on Azure Fundamentals capstone project where I designed and deployed a secure hub-and-spoke network architecture in Azure using the Azure Portal only.

The goal of this project was to move beyond theory and build something that reflects how Azure environments are actually designed in production — with private access, network security, and least-privilege principles.

# What I Built

A hub–spoke VNet architecture

Three Linux virtual machines deployed across hub and spoke VNets

Secure VM access using Azure Bastion (no public SSH)

Network Security Groups (NSGs) to control traffic flow

Azure Key Vault for secret management

Azure Blob Storage secured with a Private Endpoint

All resources were deployed and configured manually through the Azure Portal to fully understand each component.



# Architecture Summary
Networking
Component	Address Space
Hub VNet	10.0.0.0/16
Spoke VNet	10.1.0.0/16
Hub Subnet	10.0.1.0/24
Spoke Subnet	10.1.1.0/24

Virtual Machines

vm-hub-1 – Hub VNet

vm-hub-2 – Hub VNet

vm-spoke-1 – Spoke VNet
All running Ubuntu Server 22.04 LTS


## Security Design
Secure Access

SSH access is handled only through Azure Bastion

No inbound SSH ports are exposed to the internet

Public access is minimized wherever possible

# Network Security Groups

Separate NSGs applied at the subnet level

ICMP allowed only between hub and spoke VNets

SSH allowed only from Azure Bastion

This ensures controlled communication while keeping the environment locked down.

# Key Vault & Storage

Azure Key Vault used to securely store secrets

Azure Blob Storage configured with:

Public access disabled

Access allowed only via Private Endpoint

Verified that storage access works only from within the VNets

# Validation & Testing

Connected to VMs securely using Bastion

Tested private connectivity between VMs using ping

Confirmed storage account resolves to private endpoints internally

Verified NSG rules function as intended

# What I Learned

How hub–spoke architectures are implemented in Azure

Practical NSG rule design and troubleshooting

Private access patterns using Bastion and Private Endpoints

Real-world Azure networking challenges (regions, quotas, VM sizes)

# Why Security Matters in This Project

Security was treated as a first-class design principle, not an afterthought.

No public IPs: Reduces attack surface and prevents direct internet exposure.

Private networking: All communication occurs within Azure’s backbone network.

Azure Bastion: Eliminates the need for exposed SSH ports.

NSGs: Enforce least-privilege network access.

Key Vault: Protects secrets from being leaked or hard-coded.

Private Endpoints: Ensure platform services remain inaccessible from the public internet.


  





