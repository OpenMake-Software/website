---
title: Meister Insulates Your Supply Chain
description: Meister Insulates Your Supply Chain
summary: Protect your builds from hacks and errors
type: contributor
---

<div class="row">

  <div class="col">
  </div>
  <div class="col-7">
  <div style="margin-bottom:40px">
    <br>
    <h1 class="text-left">What is an insulted build supply chain?</h1>
    <hr>
    <br>
    <img src="/images/dogwithtowelonhead.jpg" alt="insulated builds" style="width:30%;height:30%" />
  </div>

Insulate your software supply chain to control the objects that are used in your software builds. A porous software compile process creates the risk of having unwanted and unnecessary artifacts in the binaries you ship to your end users. Insulating the build supply chain is essential for securing the contents of your binaries and deployment packages. To create an insulated build, the process must have precise control over the source code and external libraries that go into the build process and the resulting binaries that go into the deployment package.

The majority of software compile/link processes are done using imperative scripts written in Make, Maven, Ant, Gradle or other similar language. These scripts often use wildcard references in their logic instead of explicitly listing the needed objects. Controlling how imperative scripts reference files is an impossible task. A declarative build and package model solves this problem by adding precision into what is consumed by your build and package process.  

## The precision in insulated builds

Insulating builds requires a bit more control over the build process, specifically the management of the reference directories from which the source code and libraries are found. Your reference directories are you source and library supply chain, the raw goods that make-up your final binary and release package. Taking a look at our not so distance history in build management will give us some insights into what a tightly managed build process looks like. The VPATH (version path) used in the 'GnuMake' build tool is a great starting place for understanding how to control the objects used in your build.

Historically, the Version path (VPATH) defined a list of directories used to find both source code and libraries. The value of the  VPATH variable was used to create a list of directories that should be searched by GnuMake. If a specific file was not found in the local build directory, GnuMake would then begin searching the VPATH until it found the file, using a 'first found' logic. This type of processing generally meant that you needed to precisely specify the name of the source file and extension (foo.c), or library (foo.lib) in order for this process to work. While there were complexities around managing a VPATH, such as needing to keep the directories listed in a specific order, it did provide more control over where to find source and library files allowing project specific files to be found in the 'local' directory and reusable source and libraries to be found based on the VPATH settings. It also forced us to list the exact names of files the build required.

## The inaccuracy in the build and package step

Over time we began to move away from the concept of a VPATH. Java does use a 'Classpath' but it does not act the same as the VPATH. And they are both subject to our preference for short cuts. In some ways we just got lazy and stopped thinking of controlling the supply chain of our builds in terms of a controlled directory path. And that is not all. We stopped wanting to explicitly define the files we needed in our build, and instead took the easy method and specified file types with wildcards such as "\*.c," "\*.h", "\*.lib" "." or worse "\*.\*".  In fact, the biggest security problem with imperative build scripts is the use of wildcards - meaning pull all of the files in the directory, even if I don't know what they are or what they do. This mistake can be critical. For example, ever notice a binary that is unusually large? It might mean that libraries that were not needed were added. While using this wildcard include syntax is easy during the creation of the imperative scripts, it can cause other issues down the road. Think of the Solarwinds issue. In this case a nefarious .dll was included in the deployment package after the build. If the build/package scripts explicitly listed all of the binaries instead of using a wildcard option, telling the package process to take all files in a specific directory, just maybe the now infamous breech would not have occurred.

## Meister's Insulated Builds

Meister's insulated builds are created in two ways. First, your [build 'targets'](https://www.openmakesoftware.com/help/#!addingtargetstoyourproject.htm) are explicitly declared. Second, Meister resurrects the VPATH logic for all types of builds, not just C/C++. In Meister a VPATH is called a ['Dependency Directory.'](https://www.openmakesoftware.com/help/#!addingdirectoriestoyourdependencydirectorylist.htm) The order of the search for dependencies are also declared and can map to your lifecycle pipeline. Because Meister auto generates your build control file each time a build is executed based on these declarations, only the specified targets are created, using only the defined directories and source objects. In fact a best practice is to never pull source code or libraries from a local build directory. Referencing the local build directory (.) in the Meister Dependency Directory Path should only be used to find the intermediate objects (.objs for example) of the build. In fact, you can secure this local directory so only the Meister process has write access. All other source, libraries and artifacts should come from a version or artifact repository. Making this small change further insulates your build from including unwanted objects. At package time, the process should list all objects specifically coming only from the Meister controlled target directory. Is this overkill? Just ask someone who has had their build hacked.

Meister also provides a full Build Audit and Software Bill of Material Report. Every file used in your build is logged, even if it is not managed by a version or artifact repository, or comes from a compiler. Meister's Build Audit carefully exposes all objects used in the build so you can be 100% confident about the software supply chain that created the binaries you are sending to your end users.

## Conclusion

Deciding to allow teams to manually code their build process versus using a declarative build tool is a balance between risk and control. Imperative methods are common. Developers are familiar with doing this job and don't often think about using a more declarative method. But for all of their efforts, these scripted methods leave the build process vulnerable to both simple mistakes and malicious attacks. Declarative build solutions such as Meister provide the needed guard rails around the build process to create tighter control over what software supply chain objects are used during both the build and the subsequent packaging step of the Continuous Integration process.

Read more about Meister on our [Blogs](/blog/meister-tips/).

<h1 class="text-left">Tutorial - Define Your Dependency Directory</h1>
<hr>

This video shows how to define a list of dependency directories for controlling where build dependencies will be found along your DevOps Pipeline.

{{< youtube noYabUhVb6w >}}

  </div>
  <div class="col">
  </div>
</div>  
