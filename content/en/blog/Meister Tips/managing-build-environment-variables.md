---
title: "Build Environment Variables"
date: "2017-05-01"
categories: 
  - "meister-continuous-build"
tags: 
  - "build-environment-variables"
  - "build-management"
  - "continuous-build"
coverImage: "Meister-final-grey-stacked-white-background.png"
---

## Build Environment Variables and how to manage the details.

Build Environment Variables are critical, detailed pieces of the over build process. If you are using OpenMake Meister to manage your build you can also manage specific Environment Variables for each step.  You can also define Global variables for all steps.  In both the _Configure Machine Environment_ and _Configure Activity Environment_ fields of OpenMake Meister, you can define either variables and/or scripts to configure the environment that your machine or _Workflow Activity_ work within. Global configuration settings are the default for all _Workflow Activities_ on all machines unless you override them at this level. 

<div>
<img src="/images/Meister-final-grey-stacked-white-background-300x300.png" alt="Meister and Environment Variables" />
</div>

Configurations set at the machine level will be the default for all _Workflow Activities_ on that machine unless you override them at the _Workflow Activities_ level. You can set both machine- and _Workflow Activities_ level configurations on the _Activities Tab_ screen.  When you select a machine, _Configure Machine Environment_ appears; likewise, when you select a _Workflow Activity_ listed under the machine, _Configure Activity Environment_ appears.

## To Sum It Up

So in summary, you can set Environment Variables at 3 levels, the highest level is the Global setting.  Defines the Variable for all machines and Workflow Activities.  Secondly, you can define them at the machine or Server Pool level, and all Activities running on that machine or Server Pool will use those variables.   And within an Activity, you can assign Variables to that specific  Activity.   In our 7.5 release we will be adding an Environment Library so you can store configurations in the library and assign the library name at the Global, Workflow Activity or Machine (Server Pool) level. This allows you to more easily manage the Environment Variables and reuse them across Activities and Servers.

