# Portal

The Roar web [Portal][portal], powered by [Open OnDemand](https://openondemand.org/),
offers a visual desktop environment, file management, 
and Integrated Developer Environments (IDEs) such as Jupyter and RStudio.
[portal]: <https://portal.hpc.psu.edu>

## Selecting resources

Interactive jobs on the Portal are scheduled and managed by Slurm.
Resources to be used must be specified:
queue, number and type of nodes, number of cores, memory (RAM), run time.
For the casual user, the preset defaults are sufficient:
1 node, 4 cores, 64GB, 1 hour, open queue.

To override these defaults, check the box "Enable advanced Slurm options",
and type Slurm [resource directives][slurmdir] one per line into the text box.
[slurmdir]: slurm-scheduler.md#resource-directives

Hardware you request must be compatible with the account you specify.
If you ask for high-memory nodes, standard nodes, or GPUs, 
you need either a credit account, or a paid allocation 
that includes the requested hardware.

To use the open partition:

 - Account: open
 - Sbatch options: --partition=open

To use a [credit account](../accounts/paying-for-compute.md)
and specify a [hardware partition](../getting-started/compute-hardware.md#partitions):

 - Account: your_credit_account
 - Sbatch options: --partition=hardware_partition

To use an [allocation](../accounts/paying-for-compute.md):

 - Account: your_allocation_id
 - Sbatch options: --partition=sla-prio

!!! warning "All jobs must fit inside the resource limits of the partition they are running on"
     If resource requests exceed the partition limits, the job will not begin.

- Open queue jobs must not exceed 100 cores and 800 GB memory
- Interactive jobs must not exceed 4 cores and 24 GB memory
- Allocation limits are defined by the terms of the allocation

## Custom environments

Jupyter and RStudio Server allow the use of custom software or environments. 
To use these, select "Use custom environment" under Environment type 
and enter commands to be run when the job launches.

For example, to use a custom Anaconda environment named `myenv`, 
the "Environment setup" box should contain:

```
module load anaconda
conda activate myenv
```

For more on using Anaconda environments in your Portal jobs, 
see [Anaconda on Portal](../packages/anaconda.md/#anaconda-on-portal).
