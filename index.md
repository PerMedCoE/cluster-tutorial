## Tutorial on working with computing clusters

New to high-performance computing and unsure where to start? This tutorial provides a brief tutorial on how to access a computing cluster, learn more about managing your data and submit jobs using a batch job system.

**Note:**

The exact steps for gaining access to computing environments, managing your data, using different software and submitting jobs are specific to a given cluster. Once you know which platform you wish to work with, be sure to [**consult the relevant user documentation**](https://permedcoe.github.io/hpc-links/). 

To provide an overview of typical steps that might be involved, the following tutorial is largely based on documentation available for the CSC Mahti and Puhti clusters.

### 1. Gaining access

**First things first: the administrative part**

To gain cluster access, first one must take care of administrative tasks such as [setting up a user account](https://docs.csc.fi/accounts/). In the case of Mahti and Puhti, one would also need to either create or join a project, either as a PI or team member. For BSC resources you will need to pass through one of the calls open for researchers, you can find more information in the [how to get Supercomputing resources page](https://www.bsc.es/marenostrum/access-to-supercomputing-resources). 

**Terminal access using `ssh`**

Typically, one would use `ssh` (i.e. the secure shell protocol) to connect to a cluster. One set of instructions for this can be found on the [CSC user documentation for Mahti and Puhti](https://docs.csc.fi/computing/connecting/) or in the [MareNostrum documentation](https://www.bsc.es/user-support/mn4.php#loginnodes). If you are a Windows user, using `ssh` requires software such as [MobaXterm](https://mobaxterm.mobatek.net/) or [putty](https://www.bsc.es/user-support/mn4.php#ssh). No separate software installations are required for Linux or Mac.

Connecting using `ssh` will grant you access to the *login node* of that cluster. In addition to the login node, a cluster will also have many *compute nodes* (where the vast majority of computational work takes place). Login nodes are used for [submitting jobs to a job scheduler](#3-Submitting-jobs) and for light data processing. Heavy computing should always take place on compute nodes.

**Linux terminal commands**

Computing clusters hosted by PerMedCoE partners run on a variety of different Linux distributions. If you do not have previous experience of running Linux terminal commands, a useful tutorial can be found on [CSC docs](https://docs.csc.fi/support/tutorials/env-guide/overview/). 

### 2. Transferring and managing data

**Different data transfer options**

Once you have successfully configured your user account and gained access to the cluster, you are ready to start analyzing your data - but first, how to move the data to the cluster and back?

[Several options exist](https://docs.csc.fi/data/moving/) for moving data to and from computing clusters. Further to terminal commands like `scp` and `rsync`, one may also consider [graphical file transfer tools](https://docs.csc.fi/data/moving/graphical_transfer/) such as FileZilla. Other options for Windows or Linux can be found in the [Marenostrum4 documentation](https://www.bsc.es/user-support/mn4.php#transferringfilesonwindows). Depending on which system you are using, options for [object storage](https://docs.csc.fi/data/Allas/introduction/) may also be available.

**Where should I move my data?**

Where exactly to move the data will depend on the system in question, and how it is divided into different [disk areas](https://docs.csc.fi/computing/disk/). For example, in the case of CSC Mahti and Puhti, users have access to a personal folder with only very limited disk space (which is not shared with others). Users also have access to a research project-specific directory that is shared with other project members and has a specific quota for data storage. The case for BSC resources is very similar than CSC, having the `/gpfs/home` space restricted to the user and `/gpfs/project` open and shared between the group users. In addition, BSC provides a `/gpfs/scratch` filesystem with larger quotas and only for temporary data, without backup. More information is available in the [MareNostrum4 documentation](https://www.bsc.es/user-support/mn4.php#filesystems).

**Tips for research data management**

If you are looking for general tips on research data management, [see this tutorial on best practices](https://docs.csc.fi/data/datasets/datamanagement/).

### 3. Submitting jobs

**How do I run my analysis?**

Aside from light pre-processing that might take place on the login node, running an analysis such as a PerMedCoE workflow requires submitting a job to a job scheduler. The scheduler will place your job in a queue and eventually allocate it to a compute node(s). Almost all clusters affiliated with PerMedCoE use [Slurm](https://slurm.schedmd.com/documentation.html) for this purpose. 

Submitting jobs to a scheduler like Slurm is done using batch job scripts. For general advice and tips on how to prepare batch job scripts, [see this website](https://docs.csc.fi/computing/running/getting-started/). A universal topic to keep in mind is that submitting Slurm jobs requires an estimate of the time and computational resources required by the job in question.

Batch jobs submitted to Slurm using a batch job script are typically non-interactive. This means that once the job has been submitted, it is not possible to interact with it (e.g. through a graphical user interface). PerMedCoE workflows are also primarily based on non-interactive batch jobs submitted using a unified terminal interface available as part of the [`permedcoe` base package](https://permedcoe.readthedocs.io/en/latest/index.html).

**Where should I submit my analysis to?**

This will be system-specific. For example, CSC Mahti and Puhti use [different batch job partitions](https://docs.csc.fi/computing/running/batch-job-partitions/) depending on the anticipated duration of the job, the required resources and whether the job employs GPUs or not. To find the best way forward, refer to the [user documentation](https://permedcoe.github.io/hpc-links/) of the cluster you are working with. For BSC the limits are defined at the queue level. Depending on your granted computing time, you will be able to run with different amount of resources. To check your assigned queues in any BSC system you can run the [bsc_queues command](https://www.bsc.es/user-support/mn4.php#filesystems).

### Licence and acknowledgements

These materials were created as part of the PerMedCoE project are free cultural works licensed under a Creative Commons Attribution 4.0 International (CC BY 4.0) license.

The PerMedCoE project has received funding from the European Union’s Horizon 2020 research and innovation programme under the grant agreement Nº 951773.
