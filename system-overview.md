Release This information applies to version 1.0.7.8 and later 1.0.x versions.

For information about 1.0.7.7 and earlier versions, see 1.0. For information about 2.0 and later versions, see 2.0.
Cloud Pak for Data System overview
Last Updated: 2024-03-06
Cloud Pak for Data System is an all-in-one cloud-native Data and AI platform in a box, that enables you to collect, organize and analyze data with unprecedented simplicity and agility, within a preconfigured and governed environment. Combining storage, compute, networking and software into plug-and-play nodes, this Intel x86-based hyper-converged infrastructure helps you accelerate private cloud deployment to a matter of hours. It can easily and elastically scale to suit your changing data and AI needs. With Cloud Pak for Data System, software and system management is simplified and you benefit from a flexible pay-as-you-go capacity model.
Hardware

Cloud Pak for Data System chassis is based on Lenovo ThinkSystem SD530. The base configuration consists of two 2U Lenovo D2 enclosures, each containing four front-access SD530 servers (nodes). The enclosures are connected with a single 25G Fabric Switch and a single 1G management switch. The base configuration can be expanded when your needs grow.

Each SD530 server is a node. Each node contains four NVMe drives and the capacity of these drives defines the type of the node.
Table 1. Node type and its capacity
Enclosure type
	
Node Type
	
Raw Data Storage
Large	Large	64 TB
Node specifications:
Server type	SD530
CPU	16 cores 2.1 GHz
Total memory	192 GB
Memory DIMM	16 GB 2666 MHz DDR4
Management Network Connection	2 x 10G RJ-45
Fabric Network Connection	2x 25Gb/s Mellanox Innova-2 SmartNIC
Internal drives	

Large: 4 x 4 TB NVMe  
Note: Depending on the vendor, the NVMe drives might be 3.84 TB or 4 TB.
Internal M.2 HBA 	Marvell 88SE9230
Internal M.2 drives 	2 x 480 GB SATA
System nodes

Physical nodes are contained in enclosures. Each enclosure contains four nodes. Nodes are assigned roles. The roles are implemented by deploying one or more virtual machines on a server node.
The bare metal servers in the system host bare metal services and one or more virtual machines. Two node roles are assigned:

Control
    Three servers in a system are always assigned a control role and these three nodes are designated as a Control Plane. These servers are candidates for a Platform Manager hub. They host one Control Virtual Machine.

    Each control node is Cloud Pak for Data System master. Master nodes manage your cluster and your Cloud Pak for Data System deployment. At least two of the three control nodes must be operational for the system to work.
Worker
    Compute nodes. They can host one or more Cloud Pak for Data System Worker Virtual Machines. Worker nodes run the services in your cluster. There are two types of worker nodes:

        Universal: Can host any service, container, or pod as designated by Cloud Pak for Data System.
        Labeled: A dedicated VM to host only a specific pod or application designated by "Label".

    When a new process starts, the control plane determines which node has sufficient capacity to run the process. Cloud Pak for Data System can continue to run when multiple worker nodes fail. However, you might notice that performance decreases when multiple nodes are down.

    Additionally, if a node fails, the control plane attempts to bring any active processes up on another node. While the control plane attempts to bring up the processes, you might experience an outage.

Software

Red Hat Operating System

        World leading enterprise Linux platform
        "Military-grade" security
        High performance, high uptime

Platform Management

        System management
        System monitoring
        Events and alerts

Platform Support Elements

        HPI - Host Platform Interface
        CallHome
        Resource Managers
        ApUtil - Command line utilities to monitor and support the system
        ApComm - platform communications
        ApStor - Configuration and monitoring of platform storage resources

Netezza® Performance Server for Cloud Pak for Data System
    Available on systems with additional enclosures

        Data warehouse solution based on the same code as Netezza
        Fully compatible with Netezza appliances
        Optimized for High Performance Analytics with built-in hardware acceleration

Network

Fabric Switch (8831-25C)

Mellanox SN2410 is a 48-port 10/25 switch with 12 additional ports that can run at 10/25/40/100. It is equipped with redundant hot-swappable fans and power supplies. The switch is running Cumulus Linux.

Data Fabric Network is the active-active 25Gb connections to the Mellanox Innova-2 SmartNICs. Innova-2 is used for Netezza and Natural Language Processing acceleration.

Management Switch (8831-S52)

Edge-core AS4610-54T-O-AC-B GigE switch (8831-S52) consists of 48 x 1G RJ-45 and 4 x 10G SFP+ and 2 x 20G QFSP+ stacking ports. It is equipped with redundant hot-swappable power supplies and redundant (not hot-swappable) fans. The switch is running Cumulus Linux.

The RJ-45 connections are to the EIOM card on the enclosure. The EIOM 1Gb connections are reserved for the management network.

For more information on network configuration, see Network configuration.
Storage

For information on storage, see Platform storage.
Administrative interfaces

    System command line interface
    Netezza Performance Server web console

For more information, see Administration interfaces.

    Integrated rack
    Starting with Cloud Pak for Data System version 1.0.7.7, you can purchase a factory-built, integrated rack system that easily expands as well as streamlines the ordering process.
