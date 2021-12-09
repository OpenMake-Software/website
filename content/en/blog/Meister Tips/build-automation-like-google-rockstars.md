---
title: "Software Build Automation Done Like Google Rock Stars"
date: "2021-09-27"
categories: 
  - "meister-continuous-build"
tags: 
  - "build-automation"
  - "build-management"
  - "continuous-integration"
  - "dependency-management"
  - "google-build-process"
coverImage: "jumpinjackflash.jpg"
---

## Software Build Automation Rock Stars at Google.

Build Automation is what OpenMake Software has survived on for the last 20 years.  It is core to your software development efforts regardless of what kind of development you do - agile or waterfall. Software build automation covers all aspects of compiling and linking your software application and making sure it can support continuous delivery - knowing the readiness of any software builds.

<div>
<img src="/images/jumpinjackflash.jpg" alt="Build Automation Rock Stars" />
</div>

## Managing Dependencies

Software Build Automation includes managing software dependencies, executing incremental builds, accelerating builds, exposing analytics, showing implosion and explosion reports and simplifying the entire soup to nuts process.  Most companies use scripts. We use standardize playbooks we call Build Services. These Build Services standardize how compilers are called creating builds that are reproducible.  Google has some tips as well that I thought was worth the time seeing.

Watch this Google video from their education series.

http://www.youtube.com/watch?v=2qv3fcXW1mg

They have written a homegrown process that is extremely similar to Meister.  Build Rules, the elimination of scripts, incremental processing, management of libraries, parallelization  and distribution of workload is all shown. The good news is you do not need to write this process on your own. You can use Meister instead.  Meister solves all the problems and provides all the features covered here.   So yes, your builds can be intelligent too.

And best yet, Meister is free for small teams and can be downloaded from [https://github.com/OpenMake-Software/Meister/releases/](https://github.com/OpenMake-Software/Meister/releases/)
