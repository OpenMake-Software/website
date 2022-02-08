---
title: "Dot Net Solution Builds with Complex Dependencies"
date: "2016-12-09"
categories: 
  - "meister-continuous-build"
tags: 
  - "net"
  - "build-automation"
  - "meister"
  - "microsoft-net"
  - "microsoft-builds"
  - "msbuild"
coverImage: "Meister-final-grey-stacked-white-background.png"
---

## Dot Net Solution builds are Complicated with Multiple Solution Files.

We often get customers who have multiple Dot [Net Solutions](https://dotnet.microsoft.com/en-us//download) for creating a single application.   While Microsoft may advise against the practice, large companies tend to push the limit in software development requiring that more than one Dot Net solution file be used.  The .Net IDE cannot handle this requirement, which is were we come in.

<div>
<img src="/images/Meister-final-grey-stacked-white-background-300x300.png" alt="Meister and Environment Variables" />
</div>

OpenMake Meister can support the building of multiple Dot Net solution files, treating them as one big Dot Net solution file.  By doing this it resolves all cross solution dependencies delivering incremental builds and deploys, and accelerated .Net builds using parallel build processing.

If you need to execute a full build of multiple solutions in Meister, you simply use the .Net plug-in to create a Meister Target file for each .Net Project in the solution.  Meister will then generate a build control file that contains all projects for all solutions.  It uses MSBuild to execute the compile/link, but it manages the dependencies, incremental processing and parallel builds across the projects.

For companies who are doing large .Net builds with multiple solutions, we have seen speed improvement of up to 50% over what other build management solutions can offer such as IBM UBuild. These solutions cannot do incremental builds or build in parallel. What they do instead is have you write Nant scripts, break up the solution compiles onto different machines, and build circular until you have come to the end.  Not very efficient, but the best that can be done without doing any type of real intelligence work on the dependencies.  Products offered by Electric Cloud cannot help with this type of problem as well.  They depend on the use of GnuMake or old Nmake files that are not used by the .Net framework.

So the good news is there is a strong solution for managing multiple solution .Net files.

