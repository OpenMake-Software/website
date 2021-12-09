---
title: "Build Avoidance and Continuous Integration: Accelerating the Compile Process"
date: "2017-06-27"
categories: 
  - "meister-continuous-build"
tags: 
  - "build-automation"
  - "build-avoidance"
  - "continuous-integration"
  - "incremental-builds"
coverImage: "worksmarter.jpg"
---

## Build Avoidance - Work Smarter not Harder.

Build Avoidance is a build term that refers to the process of accelerating the compile process by not rebuilding objects that are up to date. This can improve your compile/link times substantially. Build Avoidance should be a primary function of your compile solution.

<div>
<img src="/images/worksmarter-300x200.jpg" alt="build avoidance" />
</div>

In my opinion, Build Avoidance should be a primary function of your compile solution. When used, it greatly improves the speed of your incremental builds. It is not "new" by any means. Build Avoidance was a term coined by IBM. It referred to the way ClearMake managed compiled objects. It worked then, and still works now.

## Cross Platform Build Avoidance

For most build solutions, the biggest challenge is to support build avoidance for all languages from Unix C to .Net and Java. For example, the "[gnumake](https://www.gnu.org/software/make/)" based scripting languages only supports C/C++ languages. [Maven](https://maven.apache.org/) scripting supports "pseudo incremental builds" which really is the opposite of what you would think. Maven's "pseudo incremental builds" does a "clean all" on the Projects that have changed, not on just the source code that has changed.  Doing a "clean all" is not avoiding a build, it is making sure that objects will be rebuilt by deleting them.

Meister has supported Build Avoidance for all languages for over 20 years. Only OpenMake Meister can actually make the claim for C/C++, .Net, Java and yes, even COBOL.

## Beware of False Prophets

So the moral of the story is, if your build automation tool is not supporting Build Avoidance you should look for a better build solution. Build avoidance is the process of executing a build with full knowledge of the dependencies. In addition, it understands which dependencies are out of date and need to be re-built. This is a core function of build automation. The best way to speed up a build is to not recreate objects that are already available.

## Critical to Continuous Integration: Compile and Link Process Must Work Smart

As long as we are on the topic of Build Avoidance, let's bring up how critically important it is to your Continuous Integration process. Remember - your Continuous Integration process is only as good as your build scripts.  To improve your CI process the engine that drives your compile and link process must work "smart." What does "smart" mean you ask.  A smart build knows more than you do about how your application is put together. This means that is understands the dependencies (compile, provided, system scope, etc). With those dependencies is can accurately rebuild your application by only updating what has been changed.

Yes, you can do this for Java, .Net or any native language such as C/C++. What does this buy you. First, in most cases your CI compile and link step will execute in less than a few minutes. Secondly, you are given a platform for doing pre-flight builds where any developer can re-compile the entire application, locally, without wasting an hour (or a few hours).

If you want your CI process to run really fast and accurately, make your builds "smart" so you don't have to run "clean all" every time you execute a pre-flight or CI build.  Hey it is 2017 already. Start using your computer to orchestrate your compile and link process and stop writing static scripts that lack the ability to support your development process without your constant attention. This is real build automation.
