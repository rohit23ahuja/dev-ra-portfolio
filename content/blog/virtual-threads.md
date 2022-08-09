---
title: "Virtual Threads in Java"
description: "Brief Introduction to Virtual Threads in Java. "
dateString: August 2022
draft: false
tags: ["java", "concurrency", "virtual-threads", "project-loom"]
weight: 1000
---

# The Motivation behind introducing Virtual Threads

Before Virtual Threads in Java, there was only one type of Thread i.e. Process Thread. In this article whenever we say Thread we mean to say Process Thread. A Thread is a thin wrapper over OS Thread, and 1 Thread corresponds to 1 OS Thread. This limits the scalability of a Java application because the number of threads that can be spawned by the JVM depends on the hardware capability of the system on which it is running. Modern-day applications are expected to process thousands of requests per second, so for each request, if we have to create a thread for each request we could easily hit the CPU limits of the system. Also, consider the point that in a Thread's lifecycle it might be waiting for some operation to complete (like query results from a database, etc.). In this case, it does not make much sense to block an OS-level thread.

Before going ahead, it's not as if there is no solution to the above problems. There are solutions like Reactive Programming, Event Driven Architecture, Distributed Systems, etc. But Virtual Threads help you to scale the Java application without the use of any complicated architecture and they are built in the Java API itself.

# The concept behind Virtual Threads

Compared to Threads, Virtual Threads get scheduled JVM implicit scheduler rather than solely relying on underlying OS Scheduler. Virtual Threads piggyback over a Carrier Thread (OS-level Thread) for their code execution. 
Also, The Java API has been updated to identify whether a piece of code instruction is blocking an operation. Utilizing this, a virtual thread gets removed from the carrier thread as soon as a blocking operation is encountered. And another Virtual thread is mapped to the carrier thread for its code execution. To a user and from an application's throughput perspective, this gives the benefit that a Java application can scale rapidly and easily by handling a large number of requests or tasks. 

# How to create Virtual Threads

It is optional to create a Virtual Thread. There is no need to update existing Java code that needs to be executed on Java 19 and above. For creating Virtual Thread, however, we need to call specific methods. Below are the options available:-

- Using Thread class 
  ```java 
  Thread.startVirtualThread(() -> {});
  ```
  ```java 
  Thread.ofVirtual().start(() -> {});
  ```
- Using ExecutorService unbounded Thread Pool methods
  
  ```java 
  ExecutorService executor = Executors.newVirtualThreadPerTaskExecutor();
  ```
# References
 - [Oracle Blog](https://blogs.oracle.com/javamagazine/post/java-loom-virtual-threads-platform-threads)    
 - [Oracle Blog](https://wiki.openjdk.org/display/loom/Getting+started)
 - [Oracle Blog](https://blogs.oracle.com/javamagazine/post/going-inside-javas-project-loom-and-virtual-threads)
 - [Infoq Article](https://www.infoq.com/news/2022/05/virtual-threads-for-jdk19/#:~:text=Virtual%20threads%20use%20the%20platform,benefits%20of%20a%20virtual%20thread.)