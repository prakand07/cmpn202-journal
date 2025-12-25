**Week 6 – Performance Evaluation and Analysis**

**6.1 Objective**

The objective of Week 6 was to evaluate the performance of the Ubuntu Server under different workloads and analyse system behaviour. This included measuring CPU usage, memory utilisation, disk I/O, network performance, latency, and service response times. Baseline and load testing were conducted, followed by optimisation and re-testing.


**6.2 Testing Methodology**

Performance metrics were collected using the following tools:

Metric

    CPU Usage
    Memory Usage
    Disk I/O
    Network Performance
    System Load
    Service Response

Tool Used

    top, htop
    free -h
    iostat, df -h
    ping, iperf3
    uptime
    SSH connection timing

All tests were executed via SSH from the workstation, in compliance with the administrative constraint.


**6.3 Testing Scenarios**

Baseline Performance Testing

    •	Server idle state
    
    •	Minimal background services running
    
    •	No active user load


Application Load Testing

    •	Repeated SSH connections
    
    •	Monitoring script execution
    
    •	Disk read/write activity using test files


Performance Analysis

    •	Identified CPU spikes during concurrent SSH sessions
    
    •	Disk I/O delays observed during logging operations
    
    •	Network latency remained stable due to NAT configuration


6.4 Performance Data Table

Metric

      CPU Usage
      Memory Usage
      Disk Usage
      Network Latency
      SSH Response


Baseline

    3–5%
    ~600 MB
    Minimal
    ~1 ms
    Instant


Under Load

    20–30%
    ~1.2 GB
    Moderate I/O
    ~2–3 ms
    Slight delay

**6.5 Optimisation Testing**

Two optimisations were implemented:

  1.	Disabled unnecessary background services
  
  2.	Adjusted SSH configuration to reduce authentication overhead


Results After Optimisation

    •	CPU usage reduced by ~10%
    
    •	Faster SSH response times
    
    •	Lower memory footprint


**6.6 Performance Visualisation**

Performance data was visualised using:

    •	Terminal snapshots
    
    •	Tabulated comparisons
    
    •	Monitoring script output logs

These visualisations were captured as screenshots and included in the GitHub repository.
