# random-read-performance-tool
Random Read IO Performance Tool for IRIS Data Platform

Purpose
This tool is used to generate random read Input/Output (IO) from within the database. The goal of this tool is to drive as many jobs as possible to achieve target IOPS and ensure acceptable disk response times are sustained. Results gathered from the IO tests will vary from configuration to configuration based on the IO sub-system. Before running these tests ensure corresponding operating system and storage level monitoring are configured to capture IO performance metrics for later analysis.

Methodology
Start with a small number of processes and 10,000 iterations per process. Use 100,000 iterations per process for all-flash storage arrays.  Then increase the number of processes, e.g. start at 10 jobs and increase by 10, 20, 40 etc. Continue running the individual tests until response time is consistently over 10ms or calculated IOPS is no longer increasing in a linear way.  
As a guide the following response times are usually acceptable:
  • Systems with ECP: < 8ms average random read service response times.
  • Systems without ECP: < 10ms average random read service response times.
The tool requires an empty pre-expanded IRIS.DAT database to be at least double the size of memory in the server and at least four times the storage controller cache size.
The tool uses the ObjectScript VIEW command which reads database blocks in memory so if you are not getting your expected results then perhaps all the database blocks are already in memory.
