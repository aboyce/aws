## Elastic Compute Cloud (EC2)

Provides resizable compute capacity.

New instances up in minutes, allowing rapid scaling both up and down.

Instances are created from Amazon Machine Instances (AMI).

### EC2 with Roles

- You can create EC2 Roles and permissions that are attached to an EC2 instance
- This allows AWS access natively in EC2
- They can be hot swapped/used
- Roles allow you avoid having to use Access Ids and Secrets
- Roles are preferred from a security perspective
- Policy changes take immediate effect

### Payment Options

#### On Demand

Pay a fixed rate by the hour (or second), no commitment.

#### Reserved

Capacity reservation in a 1 or 3 year contract, big discount.

#### Dedicated Host

Physical EC2 dedicated for you, can reduce licence costs if you already have them. Can be purchased on demand.

### Instance Types

#### General Purpose

Balance of compute, memory, and networking resources.

- `Mac`
- `T*`
- `M*`
- `A*`

#### Compute Optimised

Ideal for compute bound application that benefit from high performance processors.

- `C*`
- `H*`

#### Memory Optimised

Designed to delivery fast performance workloads that process large data sets in memory.

- `R*`
- `X*`
- `Z*`

#### Accelerated Computing

Use hardware accelerators, or co-processors, to perform functions, such as floating point number calculations, graphics processing, or data pattern matching, more efficiently that is possible in software running on CPUs.

- `P*`
- `D*`
- `T*`
- `I*`
- `G*`
- `F*`
- `V*`

#### Storage Optimised

Designed for workloads that require high, sequential read and write access to very large data sets on local storage.

- `I*`
- `D*`
- `H*`

### Elastic Block Store (EBS)

High-performance block-storage service designed for EC2.

Just virtual disks attached to an EC2.

Protected in availability zones.

'Root Device Volume' is the OS disk.

Can be attached to only one instance at a time.

#### Placement Groups

You can control the EC2 instance placement strategy.

- Cluster: clusters instances into a low-latency group in a single Availability Zone
- Spread: spreads instances across underlying hardware (max 7 instances per group per AZ), for critical applications
- Partition: similar to spread, it spreads the instances across many different partitions (which rely on different sets of racks) within an AZ. Scales to 100s of EC2 instances per group.

#### EBS Disk Types

##### Throughput Optimised HDD (st1)

- Low cost HDD volume, designed for frequently accessed, throughput intensive workloads
- Cannot be a boot volume
- 99.8% - 99.9% durability
- 125GB to 16TB
- 500 IOPS

##### Cold HDD (sc1)

- Lowest cost HDD volume designed for less frequently accessed workloads
- 99.8% - 99.9% durability
- 125GB to 16TB
- 250 IOPS

##### General Purpose SSD (gp2)

- Is the default volume type
- Balances price and performance for a variety of tasks
- 99.8% - 99.9% durability
- 1GB to 16TB
- 16,000 IOPS

##### General Purpose SSD (gp3)

- Lowest cost SSD that balances price and performance
- 99.8% - 99.9% durability
- 1GB to 16TB
- 16,000 IOPS

##### Provisioned IOPS SSD (io1)

- Highest performance SSD, designed for latency-sensitive workloads
- Used for NoSQL and relational databases
- 99.8% - 99.9% durability
- 4GB - 16TB
- 64,000 IOPS
- You can use this in Multi-Attach, so it is connected to multiple (up to 16) EC2 instances in the same AZ.

##### Provisioned IOPS SSD (io2)

- Highest performance and highest durability SSD, designed for latency-sensitive workloads
- Used for NoSQL and relational databases
- 99.999% durability
- 4GB - 16TB
- 64,000 IOPS
- You can use this in Multi-Attach, so it is connected to multiple (up to 16) EC2 instances in the same AZ.

##### Provisioned IOPS SSD (io2 Block Express)

- Highest performance SSD volume designed for business-critical latency-sensitive workloads
- Used for mission critical deployments of NoSQL and relational databases
- 99.999% durability
- 4GB - 64TB
- 256,000 IOPS

#### EC2 Instance Store

EBS volumes are network drives with good performance but not suitable for high performance.

For high performance you should use EC2 Instance Store. The issue is they lose their storage if they are stopped. These are good for buffers, caches, or temporary content.
