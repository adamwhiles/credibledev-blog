---
title: Linux CPU Schedulers and Why They Are Important
description: In this post we break down what CPU Schedulers are in Linux and why they are important. We also delve into CPU Scheduler options for Linux and which one may be best for Gaming on Linux.
date: 2023-12-06
created: 2023-12-06
url: /linux-cpu-schedulers-gaming-cpu-scheduler
preview: ""
draft: false
tags:
    - gaming
    - linux
categories:
    - linux
    - gaming
authors:
    - thecd
cover:
    image: images/linux-cpu-schedulers.png
---

CPU schedulers are algorithms that determine how the CPU allocates its time and resources to the processes that are running on a system. CPU schedulers are essential for ensuring that the system can perform efficiently, fairly, and responsively. Different CPU schedulers have different goals and strategies, and they can affect the performance and behavior of the system in various ways. In this blog post, I will explain why CPU schedulers are important, and compare the top three schedulers for Linux: CFS, BFS, and MuQSS.

## Why CPU Schedulers are Important
CPU schedulers are important for several reasons:

- They can improve the throughput of the system, which is the total amount of work completed per unit of time. By choosing the most suitable process for execution at each moment, the CPU scheduler can maximize the utilization of the CPU and avoid wasting time on idle or low-priority processes.
- They can reduce the waiting time and response time of the processes, which are the time intervals from when a process becomes ready to execute until it starts or finishes execution. By minimizing these time intervals, the CPU scheduler can improve the user experience and satisfaction, especially for interactive and real-time applications that require timely feedback and results.
- They can ensure fairness and balance among the processes, which means that each process receives an appropriate share of the CPU time according to its priority, workload, and resource requirements. By enforcing fairness and balance, the CPU scheduler can prevent starvation and favoritism, and maintain the stability and harmony of the system.

## How to Choose the Best CPU Scheduler for Linux
Linux is a versatile and customizable operating system that supports multiple CPU schedulers. The default CPU scheduler for Linux is the Completely Fair Scheduler (CFS), which aims to provide proportional and fair CPU time to each process based on its weight and demand. CFS uses a red-black tree data structure to keep track of the virtual run time of each process, which is the amount of CPU time that the process would have received on an ideal system with infinite CPUs. CFS selects the process with the lowest virtual run time for execution, and updates the virtual run time of the running and waiting processes accordingly. CFS also implements features such as group scheduling, load balancing, and cgroup integration to enhance its functionality and performance.

However, CFS is not the only option for Linux users. There are alternative CPU schedulers that offer different advantages and trade-offs. Two of the most popular alternatives are the Brain Fuck Scheduler (BFS), also known as the Basically Fair Scheduler, and the Multiple Queue Skiplist Scheduler (MuQSS).

BFS is a CPU scheduler that focuses on low-latency and responsiveness for desktop and interactive systems. BFS uses a single run queue for all processes, and selects the process with the highest priority for execution. BFS does not use any complex data structures or calculations, and relies on simple heuristics and timers to manage the processes. BFS also implements features such as preemption, deadline scheduling, and soft affinity to improve its performance. BFS is designed to work well for systems with up to 16 CPUs, and can handle up to 512 CPUs with some degradation.

MuQSS is a CPU scheduler that is based on BFS, but extends and improves it for modern systems. MuQSS uses multiple run queues for each CPU, and selects the process with the highest priority and the lowest latency for execution. MuQSS uses a skiplist data structure to store and access the processes, which allows for faster and more efficient operations. MuQSS also implements features such as interactivity estimation, adaptive yield, and frequency scaling to enhance its performance. MuQSS is designed to work well for systems with up to 64 CPUs, and can handle up to 2048 CPUs with some degradation.

The choice of the best CPU scheduler for Linux depends on the needs and preferences of the user and the system. There is no definitive answer, as each CPU scheduler has its own strengths and weaknesses, and may perform differently under different workloads and scenarios. However, some general guidelines are:

- If the user values fairness and proportionality over responsiveness and latency, and has a system with many CPUs and processes, CFS may be the best option.
- If the user values responsiveness and latency over fairness and proportionality, and has a system with few CPUs and processes, BFS may be the best option.
- If the user wants a balance between responsiveness and fairness, and has a system with moderate CPUs and processes, MuQSS may be the best option.

Of course, the user can also experiment with different CPU schedulers and compare their results and experiences. Linux allows the user to change the CPU scheduler at run time, by using the chrt command or the schedtool utility. The user can also compile a custom kernel with a different CPU scheduler, by using the menuconfig or xconfig tools.

## Best Linux CPU Scheduler for Gaming
There is no definitive answer to this question, as different CPU schedulers may have different effects on gaming performance depending on the system configuration, the game, and the workload. However, some general factors that may influence the choice of CPU scheduler are:

- Latency: This is the time interval from when a process becomes ready to execute until it starts execution. Low latency is desirable for gaming, as it means that the game can respond quickly to user input and events. CPU schedulers that prioritize latency over throughput, such as BFS and MuQSS, may be better for gaming than CPU schedulers that aim for fairness and proportionality, such as CFS.
- Responsiveness: This is the ability of the system to handle multiple processes and tasks without noticeable delays or lags. High responsiveness is important for gaming, as it means that the game can run smoothly and consistently without interruptions or stutters. CPU schedulers that balance the load and resources among the processes, such as CFS and MuQSS, may be better for gaming than CPU schedulers that favor a single process or task, such as BFS.
- Stability: This is the reliability and robustness of the system and the CPU scheduler. High stability is essential for gaming, as it means that the system and the game can run without crashes, errors, or glitches. CPU schedulers that are well-tested and widely-used, such as CFS, may be better for gaming than CPU schedulers that are experimental or customized, such as BFS and MuQSS.

Based on these factors, some possible recommendations are:

- If the user values low latency and responsiveness over stability and fairness, and has a system with few CPUs and processes, BFS may be the best option.
- If the user values high responsiveness and stability over low latency and fairness, and has a system with moderate CPUs and processes, MuQSS may be the best option.
- If the user values high stability and fairness over low latency and responsiveness, and has a system with many CPUs and processes, CFS may be the best option.

## How Do You Change the CPU Scheduler?
This exact process will vary between Linux distributions and is out of the scope of this article. Generally speaking, you will use a patched Linux kernel that includes the scheduler that you want to use. For example, the zen-kernel is available and popular for Linux Gaming. The Zen kernel uses the MuQSS CPU scheduler and BFQ I/O sheduler. Another example would be the Nobara Linux Distribution which uses a customized kernal that includes the BFS scheduler and BFQ I/O scheduler.

## Conclusion
CPU schedulers are important for managing the execution of processes on a system, and can affect the performance and behavior of the system in various ways. Linux supports multiple CPU schedulers, each with its own goals and strategies. The user can choose the best CPU scheduler for Linux based on their needs and preferences, or try different CPU schedulers and see what works best for them.