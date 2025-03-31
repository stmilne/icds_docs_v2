# Paying for compute

To access newer hardware including GPUs, to run jobs without risk of pre-emption,
and to run with wall times longer than the 48-hour limit on the open queue,
users must pay for comput time.

There are two ways to pay for compute time on Roar:  credit accounts, and allocations.

**Credit accounts** are like Starbucks cards:  

- you only pay for what you use; 
- you can buy time on any type of hardware you need;
- but you must stand in line with other paying customers.

**Allocations** are like vacation time-shares:  

- you reserve time on specific hardware;
- you get prompt access to your resources; 
- but you cannot use hardware different from what you reserved,
- and you must pay whether or not you use the time.

With both credit accounts and allocations, 
PIs can manage the account, adding group members to the list of allowed users.

PIs can have multiple accounts and allocations, with different user lists, 
paid by different sources of funds, for different research projects.

## Node prices

Prices for different compute nodes are set proportional to the cost of the hardware,
and at a level competitive with the cost of buying your own cluster.
More expensive nodes cost more to use, reflecting their greater value.

| node type | characteristics | credit <br> per day | allocation <br> per month |
| ---- | ---- | ---- | ---- | 
| basic | 4 GB/core | $0.096 | $1.81 |
| standard | 8 GB/core + IB | $0.178 | $3.37 |
| high | 20 GB/core + IB | 0.31 | $5.86 |
| A100 | 24 cores + 192 GB + IB | $5.97 | ask ICDS | 
| P100 | 28 cores 256 GB + IB | $0.598 | $105.67 |

Here IB = Infiniband, and GPU nodes come with some number of CPU cores.
Older P100 GPUs are ten times cheaper than A100 nodes, 
because they run about 10 times slower.

## Monitoring usage

For credit accounts:

The `get_balance` command can be used to show credit accounts and current balances.
To learn how to view details for specific accounts and people, use `get_balance --help`.

!!! warning "Request only the hardware you actually need."
	Jobs paid for by credit accounts will be charged 
	for the requested hardware, for the actual runtime of the job,
	whether or not it is actually used.

For allocations:

The `mybalance` command gives information about allocations.
For more information, get help with `mybalance -h`.


