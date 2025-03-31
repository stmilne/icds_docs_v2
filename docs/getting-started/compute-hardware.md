# Compute hardware

A cluster consists of multiple nodes connected to one or more central filesystems. 
A node is basically a single computer, roughly comparable to a powerful desktop machine. 
Some nodes are networked together with fast connections (Infiniband) that enable 
efficient communication between nodes, allowing large jobs to run in parallel on multiple nodes.
Finally, some nodes include GPUs (graphical processing units),
which can accelerate certain compute jobs.

The different types of nodes available on Roar are:

| Resource | Count | Cores | Memory <br> (GB) | CPU | CPU <br> Family | Network |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Basic | 120 <br> 240 | 64 <br> 24 | 256 <br> 128 | Gold 6430 <br> E5-2650v4 | sapphirerapids <br> broadwell | Ethernet|
| Standard | 140 <br> 156 <br> 233 | 48 <br> 48 <br> 24 | 512 <br> 384 <br> 256 | Gold 6342 <br> Gold 6248R <br> E5-2680v3 | icelake <br> cascadelake <br> haswell | Infiniband |
| GPU P100 <br> (12GB) | 8 <br> 68 | 28 | 512 <br> 256 | E5-2680v4 | broadwell| Infiniband <br> Ethernet|
| GPU A100 <br> (40GB) | 38 | 48 | 384 | Gold 6248R | cascadelake | Infiniband |
| GPU V100 <br> (32GB)| 2 | 24 | 512 | E5-2680v3 | haswell | Ethernet |
| 4xGPU V100 <br> (32GB) | 2|  24 | 512 | Gold 6132 | skylake | Ethernet |
| GPU A40 <br> (48GB) | 12 | 36 | 1024 | Gold 6354 | icelake | Ethernet |
| High Memory | 25 <br> 2 | 48 <br> 56 | 1024 | Gold 6342 <br> E7-4830v4 | icelake <br> broadwell | Infiniband |
| AMD Genoa | 36 | 64 | 384 | EPYC 9354 | Genoa | Infiniband |

## Partitions

Nodes on Roar are grouped into four different partitions:

- **basic** – CPU nodes without Infiniband, for jobs that fit on a single node.
- **standard** – CPU nodes with Infiniband (essential for multinode jobs).
- **high-memory** – CPU nodes with extra memory, for memory-intensive jobs.
- **interactive** – Nodes with graphics cards, that service the Portal.

All the various types of GPU nodes are grouped into the standard partition,
except the 12 A40 GPU nodes, which service the interactive partition.

!!!warning "To use a paid allocation, use --partition=sla-prio"
	Jobs under a paid allocation do not specify the basic, standard,
	high-memory, or interactive partitions.
	Instead, --partition=sla-prio tells the job
	to use the hardware in your allocation.