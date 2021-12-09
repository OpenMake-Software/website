---
title: "Distributed builds and Configuring Remote Agents"
date: "2017-05-07"
categories: 
  - "meister-continuous-build"
tags: 
  - "build-automation"
  - "continuous-integration"
  - "distributed-builds"
  - "server-pooling"
coverImage: "computer-network.jpg"
---

## Using Distributed Builds with Remote Agents for Continuous Integration.

Distributed builds requires the use of Remote Agents.  A common question I see on our support forums is how to configure Remote Agents to maximize machine resources. 

<div>
<img src="/images/computer-network-300x225.jpg" alt="distributed builds" />
</div>

## Configuring Remote Build Agents

When using Meister you can configure a variety of Remote Agents types including:

- Physical
- Pre-Provisioned Virtual
- Amazon EC2, HyperV, and vCenter

You can configure Remote Agents for load balancing, process utilization and <a href="https://en.wikipedia.org/wiki/Build_automation#Distributed_build_automation"> distribution </a> by setting the following parameters.

## CPU % Threshold

Used to create a weighted value for use in deciding to which machine a queued activity will be assigned during load balancing. Recommend value is 80%.   For instance, if there are two _Remote Agents_, Agent A and Agent B, a CPU % Threshold can be assigned to determine which machine to use first.

The equation for this weighted value is:

CPU  % Threshold – Current CPU % Usage

For example, if Agent A and Agent B both have a CPU % Threshold of 80%, and Agent A is currently running at 50% CPU, its weighted value will be 30. If Agent B is running at 70% CPU utilization, its weighted value will be 10. In this case, if all other settings for the two _Remote Agents_ are the same, Agent A will have the queued activities assigned to it, since it has a higher differential between CPU % threshold and current CPU % usage.

## Queue Depth Threshold

Determines how many _Workflow Activities_ will be queued up to run before the KB server starts offloading activities to other _Remote Agents_ in the _Server Pool_.  The value of this number is determined by the amount of resources available to process Workflow Activities.  You can enter a number between 1 and 200.  The initial recommended value to 10 and can be increased if additional Remote Agents are being started unnecessarily.  The higher the number, the larger the queue.

## Max # of Running Workflows

Controls how many _Workflows_ can be run simultaneously on the same _Remote Agent_.  Note: this value is different from the value set by the OMSUBMIT\_MAX\_USER\_PROC  variable, which controls how many simultaneous _Workflow_ processes can be run on a _Remote Agent_, or better known as parallelized processes.

By configuring and defining your Remote Agents to server pools you can easily maximize server resources which will improve your workflow performance and speed.
