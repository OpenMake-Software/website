---
title: "Incremental Builds are Critical for Continuous Builds"
date: "2017-06-29"
categories: 
  - "meister-continuous-build"
tags: 
  - "build-automation"
  - "continuous-integration"
  - "devops"
  - "incrmental-builds"
coverImage: "incrBuild.jpg"
---

## Incremental Builds are Critical for Fast Continuous Builds.

Incremental builds are important for managing [continuous builds](https://en.wikipedia.org/wiki/Incremental_build_model) for continuous delivery. Handing over a release from dev to prod must be easy and automated.  The production side of the house cannot always be expert in every team's application, there can be just too many in large organizations.  So one way to keep it simple is to perform incremental deploys when at all possible.  The key to incremental deploys is an incremental build.  One hand feeds the other.  In the Make world, or more specially ClearMake, this was called Build Avoidance.  It seems that the art of avoiding building objects has all been lost even though it is critical to agile developers and the DevOps process.Incremental Builds are critical for fast continuous build and breaking down waterfall barriers and adopting agile practices.]

<div>
<img src="/images/incrBuild-300x199.jpg" alt="incremental builds" />
</div>

## Break Down Waterfall Barriers with Incremental Builds

The _Build_ itself must become incremental to fully support a development process where incremental changes are encouraged.  If not, your _Continuous Integration_ process is impeded by a slow _Build_ process written to support a waterfall methodology.  Hence, a slow compile creating all binaries each time – the "big bang" approach.  When using OpenMake Meister for powering _Build_, the default _Build_ is an incremental _Build_.  Nothing special is required to execute a build using _Build Avoidance_.  Your _Build_ will automatically be executed on an incremental basis.  Therefore, you are reducing your _Build_ times down from hours to minutes.

## Reduced Build Times for Continuous Build

Incremental _Builds_ substantially decrease _Build_ times by avoiding the execution of _Build_ steps that are not needed.  This is a critical component of lean methodologies such as Agile Unified Process (Agile UP), Scrum, and Rhythm (Unified Build Infrastructure).  So, If you are looking for ways to improve _Build_ times, the use of incremental _Build_ will allow you to reach your goal.

Incremental _Builds_ determine all dependent relationships in the _Build_ regardless of language.  For Java, an incremental _Build_ determines the dependency of all .jar, .war and .ear files. This also includes jar files that are used by other jar files and their dependent java source files.   Similarly, in more traditional languages such as C/C++ or COBOL, dependency relationships are discovered for all included headers, copybooks, etc.

Note:  If you are using Meister and choose to always execute _Builds_ using a "clean all"  approach, pass the following parameters to the om process when executing your _Builds_:

\-a or clean all

If the clean all parameter is not passed, your _Build_ will be performed in the most efficient manner using [_Build_ _Avoidance._](/blog/2017/06/27/build-avoidance-and-continuous-integration-accelerating-the-compile-process/)
