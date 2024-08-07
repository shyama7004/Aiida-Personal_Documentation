# Introduction

AiiDA is an open-source Python infrastructure designed to help researchers automate, manage, persist, share, and reproduce the complex workflows associated with modern computational science and all associated data.

AiiDA is built to support and streamline the four core pillars of the ADES model: Automation, Data, Environment, and Sharing. Here are some of the key features of AiiDA explained in detail:

## Key Features

### Workflows
AiiDA allows users to build and execute complex, auto-documenting workflows. These workflows can be linked to multiple codes running on both local and remote computers. This feature ensures that computational processes are not only automated but also well-documented, making it easier to reproduce and understand the sequence of operations performed.

### High-throughput
AiiDA’s event-based workflow engine supports tens of thousands of processes per hour with full check-pointing. **High throughput** refers to the system's ability to handle and execute a large number of tasks efficiently within a short period. This capability is crucial in computational science, where large datasets and numerous calculations are routine. It enables researchers to perform extensive simulations and data analyses quickly, thus speeding up scientific discovery.

### Data Provenance
AiiDA automatically tracks and records the inputs, outputs, and metadata of all calculations and workflows in extensive provenance graphs. These graphs preserve the full lineage of all data, ensuring that every piece of data can be traced back to its origin. This feature is vital for ensuring reproducibility and transparency in scientific research, as it allows researchers to understand and verify the steps leading to any given result.

### Advanced Queries
AiiDA’s query language enables fast graph queries on millions of nodes. This means that users can quickly search and retrieve specific pieces of information from the vast amounts of data managed by AiiDA. Advanced querying capabilities are essential for efficiently handling large datasets and extracting meaningful insights.

### Plugin Interface
AiiDA supports any computational code and data analytics tool via plugins. This includes different data types, schedulers, connection modes, etc. The plugin interface makes AiiDA highly extensible and adaptable to various computational needs. Users can integrate their preferred tools and workflows, enhancing the versatility of the platform. (See the public plugin repository for available plugins.)

### HPC Interface
AiiDA can seamlessly interact with heterogeneous and remote computing resources. It works with many schedulers out of the box, including SLURM, PBS Pro, Torque, SGE, and LSF. This feature is crucial for researchers who rely on High-Performance Computing (HPC) resources to run their computations, as it ensures that AiiDA can manage and execute jobs across different HPC environments without compatibility issues.

### Open Science
AiiDA allows users to export both full databases and selected subsets. These exports can be shared with collaborators or made available and browsable online on the Archive and Explore sections of Materials Cloud. This feature promotes open science by making research data accessible to the broader scientific community, facilitating collaboration and knowledge sharing.

### Open Source
AiiDA is released under the MIT open-source license. This means that the software is freely available for anyone to use, modify, and distribute. The open-source nature of AiiDA encourages community contributions and ensures that the platform remains transparent and continually improved by a diverse group of developers and users.
