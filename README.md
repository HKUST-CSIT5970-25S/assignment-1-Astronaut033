[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/IAASVEAZ)
# CSIT5970 Assignment-1: EC2 Measurement (2 questions, 4 marks)

### Deadline: 11:59PM, Feb, 28, Friday

---

### Name: GUO Yilin
### Student Id: 21072202
### Email: yguocr@connect.ust.hk

---

## Question 1: Measure the EC2 CPU and Memory performance

1. (1 mark) Report the name of measurement tool used in your measurements (you are free to choose *any* open source measurement software as long as it can measure CPU and memory performance). Please describe your configuration of the measurement tool, and explain why you set such a value for each parameter. Explain what the values obtained from measurement results represent (e.g., the value of your measurement result can be the execution time for a scientific computing task, a score given by the measurement tools or something else).

    > In my measurements, I used Phoronix Test Suite as the measurement tool. Phoronix Test Suite is an open-source benchmarking tool widely used to measure the performance of various system components, including CPU, memory, disk, etc. I selected two specific tests to measure CPU performance and memory performance.
    > Configuration Explanation:
    > CPU Test:
    > I used the pts/compress-7zip test from Phoronix Test Suite. This test primarily measures the CPU performance through compression tasks. Specifically, it runs the 7zip compression algorithm to evaluate the CPU's capability in handling data compression tasks.
    > Command:phoronix-test-suite run pts/compress-7zip
    > Memory Test: For measuring memory performance, I used the pts/ramspeed test from Phoronix Test Suite. This test evaluates the system's memory bandwidth and performance by performing continuous read and write operations on the memory.
    > Command: phoronix-test-suite run pts/ramspeed
    > Explanation of Parameters: pts/compress-7zip: This test simulates compression tasks to evaluate the speed and responsiveness of the CPU while performing data compression. By testing the 7zip compression algorithm, it measures the computational power of the system.
    > pts/ramspeed: This test measures memory performance by performing continuous memory read and write operations, reflecting the system's memory bandwidth and responsiveness.
    > Measurement Results: CPU Performance Results: The results from the pts/compress-7zip test are given in MIPS (Million Instructions Per Second). This value represents the CPU's speed in handling compression tasks. A higher value indicates better CPU performance.
    > Memory Performance Results: The results from the pts/ramspeed test are measured in MB/s (MegaBytes per second). This value indicates the memory bandwidth, i.e., the amount of data that can be read or written per second. Higher bandwidth values indicate better memory performance.
    > Interpretation of Results: CPU Performance: The results from this test represent the CPU's efficiency in executing compute-intensive tasks like compression. Higher MIPS values indicate faster CPU performance and the ability to handle demanding computational tasks more efficiently.
    > Memory Performance: Memory performance reflects the system's ability to handle large data sets by providing high memory throughput. Higher memory bandwidth allows faster processing of large amounts of data, making the system suitable for memory-intensive tasks.
    > Application of Results: These measurement results can be used to estimate the execution time of scientific computing tasks. For instance, systems with higher CPU performance will complete computational tasks faster, and systems with better memory bandwidth can handle larger data sets more efficiently. Therefore, both CPU performance and memory performance directly affect the efficiency of scientific computing and big data processing tasks.

2. (1 mark) Run your measurement tool on general purpose `t2.micro`, `t2.medium`, and `c5d.large` Linux instances, respectively, and find the performance differences among these instances. Launch all the instances in the **US East (N. Virginia)** region. Does the performance of EC2 instances increase commensurate with the increase of the number of vCPUs and memory resource?

    In order to answer this question, you need to complete the following table by filling out blanks with the measurement results corresponding to each instance type.

    | Size        | CPU performance | Memory performance |
    | ----------- | --------------- | ------------------ |
    | `t2.micro`  |    3614 MIPS    |    10828.01 MB/s   |
    | `t2.medium` |    3649 MIPS    |    10843.57 MB/s   |
    | `c5d.large` |    7431 MIPS    |    13714.99 MB/s   |

    > Region: US East (N. Virginia). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI.

## Question 2: Measure the EC2 Network performance

1. (1 mark) The metrics of network performance include **TCP bandwidth** and **round-trip time (RTT)**. Within the same region, what network performance is experienced between instances of the same type and different types? In order to answer this question, you need to complete the following table.

    | Type                      | TCP b/w (Mbps) | RTT (ms) |
    | ------------------------- | -------------- | -------- |
    | `t3.medium` - `t3.medium` |                |          |
    | `m5.large` - `m5.large`   |                |          |
    | `c5n.large` - `c5n.large` |                |          |
    | `t3.medium` - `c5n.large` |                |          |
    | `m5.large` - `c5n.large`  |                |          |
    | `m5.large` - `t3.medium`  |                |          |

    > Region: US East (N. Virginia). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI. Note: Use private IP address when using iPerf within the same region. You'll need iPerf for measuring TCP bandwidth and Ping for measuring Round-Trip time.

2. (1 mark) What about the network performance for instances deployed in different regions? In order to answer this question, you need to complete the following table.

    | Connection                | TCP b/w (Mbps) | RTT (ms) |
    | ------------------------- | -------------- | -------- |
    | N. Virginia - Oregon      |                |          |
    | N. Virginia - N. Virginia |                |          |
    | Oregon - Oregon           |                |          |
 
    > Region: US East (N. Virginia), US West (Oregon). Use `Ubuntu Server 22.04 LTS (HVM)` as AMI. All instances are `c5.large`. Note: Use public IP address when using iPerf within the same region.
